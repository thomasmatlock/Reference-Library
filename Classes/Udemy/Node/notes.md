Node

- Jonas Node - Node.js, Express, MongoDB & More: The Complete Bootcamp 2019 (jonas) #copy

  - Welcome
  - Intro to Nodejs and NPM

    - Section Intro
    - What Is Node.js and Why Use It?

      - runtime: basically a container or environment that js can be run in, or executed inside
      - Pros
        - nodejs is single-threaded, non blocking, event driven, I/O model
      - Use cases
        - API w database behind it, preferably noSQL
        - Data streaming (youtube, twitch)
        - realtime chat apps
        - server side web apps

    - Running Javascript Outside the Browser
      - Ctrl + L // clears the console while in node
      - Ctrl + D // exits node, just like .exit
      - Hit Tab twice // displays all global variables
        - You will see some new modules, like https, fs, crypto, etc
      - Underscore = include previous results
        - Example:
          - 2+2
          - 4
          - \_+2
          - 6 // it includes the previous result, without having to type it
      - Tab twice on a a property or module, you can see all the functions available to it
        - example:
          - String.<TabTab> // displays a few dozen or so methods we use on it
    - Using Modules 1: Core Modules
      - So, we made an index.js file and logged 'hello world'
      - instead of entering 'node', then hitting enter, instead we follow 'node' w filename, ie:
        - node index.js
      - also, for help later, goto nodejs site/docs/ and versions are on left nav column, choose version you are using
    - Reading and Writing Files
    - Blocking and Non-Blocking: Asynchronous Nature of Node.js
      - Synchronous = processed in order, line by line
      - Synchronous code = blocking code, asynchronous code = non blocking. Async is faster, optimized
      - each line has to wait for execution of previous line
      - this can be a problem for slow code, like an API request
    - Reading and Writing Files Asynchronously
    - Creating a Simple Web Server
      - a
    - Routing
      - url = host:port/subpage
      - without routing, no matter what the subpage, it will always display host:port
      - routing changes that to serve different response based on request
    - Building a (Very) Simple API
    - HTML Templating: Building the Templates
    - HTML Templating: Filling the Templates
    - Parsing Variables from URLs
    - Using Modules 2: Our Own Modules
    - Introduction to NPM and the package.json File
    - Types of Packages and Installs
    - Using Modules 3: 3rd Party Modules
    - Package Versioning and Updating
    - Setting up Prettier in VS Code
    - Recap and What's Next

  - Intro to Backend Web Development

    - Section Intro

      - Part 1 (DNS lookup)
        - client/browser sends request to server
        - server sends backa a response
          - this is called the request/response model, also the client/server architecture
        - google.com, for example is not the actual address of what we want, its just an easy name to memorize
        - domain name are converted to the actual address, ie the IP, by DNS, or domain name server
          - dns is the phonebook of the internet, you have a domain, it will find you the matching domain name
            - so in order
              - protocol (https/http)
              - domain name/IP address
              - resource (domain sub page)/port (https default is 443, http is 80
                - ports are basically sub-addresses)
      - Part 2

        - TCP/IP socket connection is established between the client and server
          - connection is kept alive for entire time it takes to transfer
            - TCP is transmission control protocol
            - IP is internet protocol

      - Part 3
        - HTTP request
          - HTTP is just a protocol that allows two or more parties to communicate
            - example:
              - GET /maps HTTP/1.1 // this is the start line, HTTP method,request target,HTTP version
              - HTTP request headers //Host,User-Agent, etc
              - BODY // bodies are only used in use cases of sending data, like POST
      - Part 4

        - HTTP response

          - looks similar to the request

            - start line //HTTP1.1 200 OK // http version + status code + status message
            - headers
            - body, we already used this earlier with res.end, its usually html or files of some kind coming back

      - Step 5

        - files are rendered
        - html first, then css, js, images etc

      - job of TCP is to break up request into hundreds of chunks called packets before they are sent
      - once it arrives at destination, it will reassemble all packets into their original format

    - An Overview of How the Web Works
    - HTTP in Action
    - Front-End vs. Back-End Web Development
      - server is just a computer that has the website files, and is running an HTTP server (basically a bridge) to receive and respond to browser requests
      - static servers just hold files and respond to requests
      - dynamic servers are ones that also talk to databases, etc, you need a 3rd piece, kind of like we just wrote in the node farm thing
      - this makes it dynamic, and rather serving, it interacts and updates, stores user data, etc
        - handle payments
        - send emails
        - create user profiles
        - perform logins
        -
    - Static vs Dynamic vs API

- How Nodejs Works, A Look behind the scenes

  - Section Intro
  - Node, V8, Libuv and C++
  - Processes, Threads and the Thread Pool

    - when we use use node.js it means that there is a node process running on the computer
    - node runs in a single thread, which is basically just a sequence of instructions
    - single thread poses a problem, because its blockable, and 1 user is fine, but 10 or 10000 is a problem
    - Flow:

      - initialize program
      - execute top level code
      - require modules
      - register event callbacks
      - start event loop
        - the event loop is where pretty much everything happens
      - however, some events are too heavy to be handled by event loop, so we use thread pooling
      - thread pool gives us +4 threads, configurable up to 128 threads
      - event loop automatically offloads events to thread pool, its not us developers who decide what goes to thread pool
        - thread pool handles heavy tasks like:
          - cryptography
          - compression
          - DNS lookups
          - file system APIs

  - The Node.js Event Loop

    - event loop is heart of node.js
    - runs all code inside callback functions (non toplevel code)
    - nodejs is built around callback functions, functions that are called as soon as some work is finished
    - Event driven architecture
      - Events are emitted
      - Event loops pick them up
      - callbacks are called
        - Event examples
          - new http request
          - timer expired
          - finished file read
    - event loop does orchestration
    - Event Loop in detail

      - EL has multiple phases
      - each phase in the event loop has its own callback queue
      - phases
        - expired timers
        - IO polling and callbacks, when the previous phase is done, it returns to polling for new IO
          - in nodejs context, IO generally means networking and file access
        - setImmediateCallbacks
          - something to use in more advanced cases
        - close callbacks
      - after each phase, if there are any callbacks, those will be executed immediately
      - a tick in an event loop is just one cycle
      - before with nodemon, we were basically running an IO task, so it never exited the event loop. it just kept listening for http input
      - event loop is what makes nodejs awesome and unique, you only need event loop and thread pool, its pretty cool

    - TIPS to not block the event loop
      - Dont use sync versions of function is fs, crypto, and zlib (compression) modules in your callback functions
      - dont perform complex calculations (loops inside loops)
        -be careful w JSON in large objects
        - Dont use too highly nested regular expressions, eg nested quantifiers

* The Event Loop in Practice
* Events and Event-Driven Architecture
* Events in Practice
* Introduction to Streams
* Streams in Practice
* How Requiring Modules Really Works
* Requiring Modules in Practice

* [Optional] Async JS: Promises and Async/Await
  - Section Intro
  - The Problem with Callbacks: Callback Hell
  - From Callback Hell to Promises
  - Building Promises
  - Consuming Promises with Async/Await
  - Returning Values from Async Functions
  - Waiting for Multiple Promises Simultaneously
* Express: Start Building the Natours API
  - Section Intro
  - What is Express?
  - Installing Postman
  - Setting up Express and Basic Routing
  - APIs and RESTful API Design
  - Starting Our API: Handling GET Requests
  - Handling POST Requests
  - Responding to URL Parameters
  - Handling PATCH Requests
  - Handling DELETE Requests
  - Refactoring Our Routes
  - Middleware and the Request-Response Cycle
  - Creating Our Own Middleware
  - Using 3rd-Party Middleware
  - "Implementing the ""Users"" Routes  "
  - Creating and Mounting Multiple Routers
  - A Better File Structure
  - Param Middleware
  - Chaining Multiple Middleware Functions
  - Serving Static Files
  - Environment Variables
  - Setting up ESLint + Prettier in VS Code
* Intro to MongoDB
  - Section Intro
  - What is MongoDB?
  - Installing MongoDB on macOS
  - Installing MongoDB on Windows
  - Creating a Local Database
  - CRUD: Creating Documents
  - CRUD: Querying (Reading) Documents
  - CRUD: Updating Documents
  - CRUD: Deleting Documents
  - Using Compass App for CRUD Operations
  - Creating a Hosted Database with Atlas
  - Connecting to Our Hosted Database
* Using MongoDB w Mongoose
  - Section Intro
  - Connecting Our Database with the Express App
  - What Is Mongoose?
  - Creating a Simple Tour Model
  - Creating Documents and Testing the Model
  - Intro to Back-End Architecture: MVC, Types of Logic, and More
  - Refactoring for MVC
  - Another Way of Creating Documents
  - Reading Documents
  - Updating Documents
  - Deleting Documents
  - Modelling the Tours
  - Importing Development Data
  - Making the API Better: Filtering
  - Making the API Better: Advanced Filtering
  - Making the API Better: Sorting
  - Making the API Better: Limiting Fields
  - Making the API Better: Pagination
  - Making the API Better: Aliasing
  - Refactoring API Features
  - Aggregation Pipeline: Matching and Grouping
  - Aggregation Pipeline: Unwinding and Projecting
  - Virtual Properties
  - Document Middleware
  - Query Middleware
  - Aggregation Middleware
  - Data Validation: Built-In Validators
  - Data Validation: Custom Validators
* Error Handling w Express
  - Section Intro
  - Debugging Node.js with ndb
  - Handling Unhandled Routes
  - An Overview of Error Handling
  - Implementing a Global Error Handling Middleware
  - Better Errors and Refactoring
  - Catching Errors in Async Functions
  - Adding 404 Not Found Errors
  - Errors During Development vs Production
  - Handling Invalid Database IDs
  - Handling Duplicate Database Fields
  - Handling Mongoose Validation Errors
  - Errors Outside Express: Unhandled Rejections
  - Catching Uncaught Exceptions
* Authentication Authorization and Security
  - Section Intro
  - Modelling Users
  - Creating New Users
  - Managing Passwords
  - How Authentication with JWT Works
  - Signing up Users
  - Logging in Users
  - Protecting Tour Routes - Part 1
  - Protecting Tour Routes - Part 2
  - Advanced Postman Setup
  - Authorization: User Roles and Permissions
  - Password Reset Functionality: Reset Token
  - Sending Emails with Nodemailer
  - Password Reset Functionality: Setting New Password
  - Updating the Current User: Password
  - Updating the Current User: Data
  - Deleting the Current User
  - Security Best Practices
  - Sending JWT via Cookie
  - Implementing Rate Limiting
  - Setting Security HTTP Headers
  - Data Sanitization
  - Preventing Parameter Pollution
* Modelling Data and Advanced Mongoose
  - Section Intro
  - MongoDB Data Modelling
  - Designing Our Data Model
  - Modelling Locations (Geospatial Data)
  - Modelling Tour Guides: Embedding
  - Modelling Tour Guides: Child Referencing
  - Populating Tour Guides
  - Modelling Reviews: Parent Referencing
  - Creating and Getting Reviews
  - Populating Reviews
  - Virtual Populate: Tours and Reviews
  - Implementing Simple Nested Routes
  - Nested Routes with Express
  - Adding a Nested GET Endpoint
  - Building Handler Factory Functions: Delete
  - Factory Functions: Update and Create
  - Factory Functions: Reading
  - Adding a /me Endpoint
  - Adding Missing Authentication and Authorization
  - Importing Review and User Data
  - Improving Read Performance with Indexes
  - Calculating Average Rating on Tours - Part 1
  - Calculating Average Rating on Tours - Part 2
  - Preventing Duplicate Reviews
  - Geospatial Queries: Finding Tours Within Radius
  - Geospatial Aggregation: Calculating Distances
  - Creating API Documentation Using Postman
* Server-Side Rendering w Pug Templates
  - Section Intro
  - Recap: Server-Side vs Client-Side Rendering
  - Setting up Pug in Express
  - First Steps with Pug
  - Creating Our Base Template
  - Including Files into Pug Templates
  - Extending Our Base Template with Blocks
  - Setting up the Project Structure
  - Building the Tour Overview - Part 1
  - Building the Tour Overview - Part 2
  - Building the Tour Page - Part 1
  - Building the Tour Page - Part 2
  - Including a Map with Mapbox - Part 1
  - Including a Map with Mapbox - Part 2
  - Building the Login Screen
  - Logging in Users with Our API - Part 1
  - Logging in Users with Our API - Part 2
  - Logging in Users with Our API - Part 3
  - Logging out Users
  - Rendering Error Pages
  - Building the User Account Page
  - Updating User Data
  - Updating User Data with Our API
  - Updating User Password with Our API
* Advanced Features Payments Email File Uploads
  - Section Intro
  - Image Uploads Using Multer: Users
  - Configuring Multer
  - Saving Image Name to Database
  - Resizing Images
  - Adding Image Uploads to Form
  - Uploading Multiple Images: Tours
  - Processing Multiple Images
  - Building a Complex Email Handler
  - Email Templates with Pug: Welcome Emails
  - Sending Password Reset Emails
  - "Using Sendgrid for ""Real"" Emails  "
  - Credit Card Payments with Stripe
  - Integrating Stripe into the Back-End
  - Processing Payments on the Front-End
  - Modelling the Bookings
  - Creating New Bookings on Checkout Success
  - Rendering a User's Booked Tours
  - Finishing the Bookings API
  - Final Considerations
* Setting Up Git and Deployment
  - Section Intro
  - Setting Up Git and GitHub
  - Git Fundamentals
  - Pushing to GitHub
  - Preparing Our App for Deployment
  - Deploying Our App to Heroku
  - Testing for Secure HTTPS Connections
  - Responding to a SIGTERM Signal
  - Implementing CORS
  - Finishing Payments with Stripe Webhooks
