# Devploy
TU Dev's application hosting platform powered by docker and azure.

# Client
## Session Management
### Logging In
```
$ devploy login
```
Logs user into the platform, prompts for credentials:
```
$ devploy login
email: guy@temple.edu
password: ********
```
Only @temple.edu addresses are allowed on the platform, and user provisioning is performed by the admin of the cluster.
```
$ devploy login
\ Authenticating...
```
Performs the authentication via the the cluster controller.
```
$ devploy login
✓ Logged in successfully
```
Once logged in, the client stores session token in local dotfile to manage the session.  

### Logging Out
```
$ devploy logout
```
Logs out of the platform by deleting token from dotfile.

## SSH Keys
```
$ devploy keys
```
### Add Key
```
$ devploy keys add <path_to_key>
```
Adds an RSA private key to the authenticated account
### Lists Keys
```
$ devploy keys list
```
Lists all currently recorded keys
### Delete Key
```
$ devploy keys delete <path_to_key>
```
Deletes an SSH key

## Applications
```
$ devploy apps
```
### Create Application
```
$ devploy apps create
```
Turns the local repository into an application. The application gets an application id, and a new remote in the repository called "devploy". Application specific commands must be called from the directory in which `create` was called. The application is also immediately deployed. NOTE: this command will fail if no keys are currently added to the currently authenticated user's account.
### Lists Applications
```
$ devploy apps list
```
Lists all currently deployed applications by name and know folder name and any other repository information that is currently know about it.
### Delete Application
```
$ devploy apps delete
```
Deletes the application that was created in the current directory. Also undeploys the application and removes the git remote from the repository.

## Application Domains
```
$ devploy domains
```
### Add Domain
```
$ devploy domains add <some.domain>
```
Adds a specific domain to the application created in the current directory.  
Domain can either be:
 - A devploy subdomain (name.devploy.io) *OR*
 - Some other domain altogether (thing.com)  

### List Domains
```
$ devploy domains list
```
Lists all domains currently registered to the application created in the current directory.
### Delete Domain
```
$ devploy domains delete <some.domain>
```
Deletes a specific domain from the application created in the current directory.

## Databases
```
$ devploy dbs 
```
### Postgres
```
$ devploy dbs postrges
```
#### PSQL
```
$ devploy dbs postgres shell
```
Starts a `psql` session in your shell. NOTE: this will not work if psql is not currently installed.
#### List Owned Databases
```
$ devploy dbs postgres databases
```
Lists all owned postgres databases for a the currently authenticated user.
### Mongo DB
```
$ devploy dbs mongodb
```
#### Mongo Shell
```
$ devploy dbs mongodb shell
```
Starts a `mongo` session in your shell. NOTE: this will not work if mongo is not currently installed.
```
$ devploy dbs mongodb databases
```
Lists all owned mongo databases for a the currently authenticated user.
