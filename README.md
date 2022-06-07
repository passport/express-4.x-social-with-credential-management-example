# todos-express-social-credential-management

This app illustrates how to use [Passport](https://www.passportjs.org/) with
[Express](https://expressjs.com/) to sign users in with [Google](https://www.google.com/),
[Facebook](https://www.facebook.com/), and [Twitter](https://twitter.com/).  It
takes the [baseline example](https://github.com/passport/todos-express-social)
and extends it with [Credential Management](https://www.w3.org/TR/credential-management-1/),
allowing the browser to assist with the storage and selection of social network
accounts.  Use this example as a starting point for your own web applications.

## Quick Start

To run this app, clone the repository and install dependencies:

```bash
$ git clone https://github.com/passport/todos-express-social-credential-management.git
$ cd todos-express-social-credential-management
$ npm install
```

This app requires credentials from Google, Facebook, and Twitter.

Once credentials have been obtained, create a `.env` file and add the following
environment variables:

```
GOOGLE_CLIENT_ID=__INSERT_GOOGLE_CLIENT_ID_HERE__
GOOGLE_CLIENT_SECRET=__INSERT_GOOGLE_CLIENT_SECRET_HERE__
FACEBOOK_CLIENT_ID=__INSERT_FACEBOOK_APP_ID_HERE__
FACEBOOK_CLIENT_SECRET=__INSERT_FACEBOOK_APP_SECRET_HERE__
TWITTER_CONSUMER_KEY=__INSERT_TWITTER_API_KEY_HERE__
TWITTER_CONSUMER_SECRET=__INSERT_TWITTER_API_SECRET_KEY_HERE__
```

Start the server.

```bash
$ npm start
```

Navigate to [`http://localhost:3000`](http://localhost:3000).

## Overview

This app illustrates how to build a todo app with sign in functionality using
Express, Passport, and the [`passport-google-oidc`](https://www.passportjs.org/packages/passport-google-oidc/),
[`passport-facebook`](https://www.passportjs.org/packages/passport-facebook/),
and [`passport-twitter`](https://www.passportjs.org/packages/passport-twitter/)
strategies.

This app is a traditional web application, in which application logic and data
persistence resides on the server.  HTML pages and forms are rendered by the
server and client-side JavaScript is kept to a minimum.

This app is built using the Express web framework.  Data is persisted to a
[SQLite](https://www.sqlite.org/) database.  HTML pages are rendered using [EJS](https://ejs.co/)
templates, and are styled using vanilla CSS.

When a user first arrives at this app, they are prompted to sign in.  To sign
in, the user is redirected to their choice of Google (using OpenID Connect),
Facebook (using OAuth 2.0), or Twitter (using OAuth 1.0a).  Once authenticated,
a login session is established and maintained between the server and the user's
browser with a cookie.

The sign in page is progressively enhanced with JavaScript in order to utilize
the Credential Management API.  For browsers that support it, the user is offered
the option to store their preferred social network account making it easy to
select when they later return to the app.

After signing in, the user can view, create, and edit todo items.  Interaction
occurs by clicking links and submitting forms, which trigger HTTP requests.
The browser automatically includes the cookie set during login with each of
these requests.

When the server receives a request, it authenticates the cookie and restores the
login session, thus authenticating the user.  It then accesses or stores records
in the database associated with the authenticated user.

## Next Steps

* Add passwordless.

  Study [todos-express-webauthn](https://github.com/passport/todos-express-webauthn)
  to learn how to let users sign in with biometrics or a security key.

## License

[The Unlicense](https://opensource.org/licenses/unlicense)

## Credit

Created by [Jared Hanson](https://www.jaredhanson.me/)
