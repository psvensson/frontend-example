# Example front-end app with loign button - written in Polymer

This is a JavaScript based project using the Polymer web component framework from Google to show
 how to implement a simple log-in widget that authenticates users using the excellent Auth0 (https://auth0.com) Authentication aggregation service.


##### Prerequisites

Install the [Polymer CLI](https://github.com/Polymer/polymer-cli) using
[npm](https://www.npmjs.com) (we assume you have pre-installed [node.js](https://nodejs.org)).

    npm install -g polymer-cli

Second, install [Bower](https://bower.io/) using [npm](https://www.npmjs.com)

    npm install -g bower
    
You will also need an Auth0 account and a configured project (called client in Auth0) where the client secret and domain have to be configured inside the login-widget component.    

![Image of Client](https://cdn2.auth0.com/docs/media/articles/architecture-scenarios/server-api/non-interactive-client.png)

![Image of Client](http://ga4gh-server.readthedocs.io/en/stable/_images/auth0-create-client-details.png)

##### Initialize project and download project-specific dependencies

    npm install
    bower install

### Start the development server

This command serves the app at `http://localhost:8080` and provides basic URL
routing for the app:

    polymer serve --open

### Important parts
This project shows how to create a Polymer web component which uses the Auth0 service to login a user, and which then sends the access token obtained from Auth0
to a server back-end which can verify the token and return a proper user object back to the component.
 
The component then expose this object to my-app, which in turn wires any changes to the my-view1 component (it displays the user name).
Localstorage is use to save a session id which is assumed to be present on the returned user object, and another call to the server
 wil be made if the page is reloaded and the session id is prsent to reload the user object directly without having to
 login again.

The file index.html loads the web component framework and contains the app starting component, which contain everything else - my-app.

Almost everything in this app comes directly from one of the polymer-cli created starting PRPLE project. 
The only additions are the login widget and a convenience erapper for Ajax calls to the server-side.
