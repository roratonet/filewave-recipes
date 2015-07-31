# FileWave & AutoPkg
FileWave specific recipes for AutoPkg.  These recipes allow FileWave admins to
import applications as filesets or pkgs into FileWave, ready for deployment to
test machines. 

Our aim was to avoid replicating existing recipes and as such most of the
recipes will use a parent recipe that is already in the standard autopkg repo.

## Pre-requisites
The following is *required* in order to use these recipes: 

1. On the machine that runs autopkg you must have a copy of FileWave Admin 10.0
or greater installed.
1. AutoPkg 0.5.0 or greater.

The FileWave autopkg recipes rely on having access to the FileWave Admin 
Command Line features which are part of the FileWave Admin application.

You can confirm that you have the right version by running the FileWave Admin
Command Line from the Terminal, for example:

    $ /Applications/FileWave/FileWave\ Admin.app/Contents/MacOS/FileWave\ Admin -v
    10.0.0
    $

## Required Configuration
The recipes and processors need to know where the FileWave Server is located.  

To do this, the following environment variables can be used:

1. FW_SERVER_HOST - defaults to 'localhost', can be hostname or IP address
1. FW_SERVER_PORT - defaults to 20016
1. FW_ADMIN_USER - defaults to 'fwadmin', its the name of the account that will be used to connect
1. FW_ADMIN_PASSWORD - defaults to 'filewave', its the password of the FW_ADMIN_USER account
 
## FW_ADMIN_USER Permissions
FileWave is multi-user capable.  For security reasons - we *strongly* 
recommend creating another user for use with AutoPkg.  So much so that if
  you insist on using the fwadmin user - the program will print out
  annoying warnings indicating that you are making use of the super-user
  account.

You should create a user called 'autopkg' and then give this 
user the following rights: 
 - Update Model
 - Modify Clients/Groups
 - Modify Filesets
 - Modify Associations
 - Modify Imaging Associations
  
Then on the machine running autopkg, set the FW_ADMIN_USER value:

    defaults write com.github.autopkg FW_ADMIN_USER api
    


