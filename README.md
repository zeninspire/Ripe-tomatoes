# Ripe-tomatoes
Restaurant information agregator

#Why Ripe Tomatoes
  1. Create awesome shit
    - Work on an app that can be used by consumers on a daily basis
    - Easy to set layerable short-term and long-term goals--very little all/nothing milestones
  2. Create that shit quickly
    - Thorough documentation and comments
    - Modularized code
    - Zhao
  3. Get better at shit
    - Wide range of challenges, from MVC and Angular to databases and tokens. APIs, callbacks/async functions. Front-end and back-end.

#Getting Started
We are excited that you have chosen to contribute to the Ripe Tomatoes project! Ripe Tomatoes was designed to be highly modular and easily expandable. Notable things include:
- Clearly divided client and server side code with data transactions between the two kept to a minimum
- Auto-deployment to heroku server 
- Modularized API functions to easily add additional API calls asynchronously, minimizing server time and development time

#Data flow 
Search query:
  1. User makes an inquiry for a given keyword and location
  2. Clientside sends a post request from '/search' with keyword and location to server
  3. Server processes the request and asynchronously sends out API requests to foursquare and yelp
  4. After foursquare and yelp API fetches are complete, server compares the results of the API and combines the results into one array called matchedRestaurants.
  5. Once the array is complete, server sends a Google API request for each restaurant in the array. These requests (1 per restaurant) are done async to minimize time. The restaurant array is then updated with the Google API information
  6. Server then sends the results of the search back to the client
  7. Client handles the data and renders it appropriately
  
  Relevant backend files: 
- server/server.js (starts the server and database)
- server/config/requestHandlers.js (handles requests)
- server/config/utils.js (all of the helper functions, API calls, and comparison functions)
  Relevant frontend files:
- client/app.js (main angular functions)
- client/searchResults.html (handles the results after server responds)

User login:
  1. User creates a new username/password
  2. Client sends information to server
  3. Server checks if username exists, adds user + encrypted/hashed pw to MongoDB. User's favorites can now be stored
  4. Token-based session created for user--user automatically signed in
  
  Relevant backend files: 
  - server/server.js (starts the server and database)
  - server/config/requestHandlers.js (handles requests)
  - server/users/userController.js (handles all the functions related to user actions like sign-in, addFavorites, etc)
  - server/users/userModel.js (defines user schema and password functions)
  Relevant frontend files:
  - client/app.js (main angular functions)
  - client/signin.html
  - client/signup.html

#First steps
1. Get your own damn API keys:
  - Yelp: https://www.yelp.com/developers/documentation/v2/overview   ----> "Manage API Access"
  - Foursquare: https://developer.foursquare.com/ ----> "Get started"
  - Google Places API: https://developers.google.com/places/ 
  - Google Map API: https://developers.google.com/maps/?hl=en
2. Replace the API keys in apiKeys.js with your new keys (if the file doesn't exist, create one just like the apiKeys_example.js and rename it apiKeys.js in the same location)
3. npm install, [sudo] mongod, nodemon server/server.js
4. In browser, go to 127.0.0.1:3000
5. Follow the data flows as outlined above to understand the current structure and functions
6. Ask Zhao for any help