AUTHOR: William Stein, April 2012

This is a very simple test implementation of an idea for how to create
the Sage Workspace Server to see if it has any legs.  Key to the idea
is that the implementation is very plugable and iterative, so this is
a good place to begin.  The following is thus the simplest imaginable
version of the architecture.  My plan is to make a version of this
with no shortcuts or ugly code that is fully documented.

The Data Model:

- user:
    - name
    - exactly one workspace
- workspace:
    - name
    - file = exactly one code evaluator
- session server:
    - name
    - url

The Session Server:
- flask webserver:
    - request a session
         INPUT:  url
         OUTPUT: session id
    - submit block of code to evaluate (get back id)
         INPUT:  session id, block of code (string)
         OUTPUT: code id
    - as code generates output, the session url will receive
      POST requests containing the output so far and code id

The Sage Workspace Server:
- gae flask webserver:
    - user login
    - / is: POST form to input code to evaluate in the only object in the only workspace
    - create channel to client
    - receive block of code to evaluate
    - if no sage session for user, 
    
The User Client:
- javascript in a client browser:
    - submit code to evaluate
    - put output somewhere as it is appears








