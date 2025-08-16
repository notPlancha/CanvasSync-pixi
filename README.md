## Branch note
This branch de-implements encryption.

## Fork note
This fork is intended for pixi users. Just clone the repo and run `pixi run canvas`.

Also, this fork also implements some chanegs to try and keep going even after failing on some files and implements [#46](https://github.com/perslev/CanvasSync/pull/46);
if you don't want this changes use the no-changes branch.

# CanvasSync
Synchronise modules, assignments and files located on a Canvas by Instructure web server to your local computer.

Description
-----------
CanvasSync helps students automatically synchronize modules, assignments & files located on their institutions Canvas web server
to a mirrored folder on their local computer. It traverses the folder hierarchy in Canvas from the top course level down to individual
files and creates a similar folder structure on the local computer:

![](resources/overview.png)

First, CanvasSync creates a folder hierarchy on the local computer reflecting the 'Modules' section on the Canvas server.
Files are stored in folders such as ../SyncFolder/Course/Module/SubFolder/file.txt. Both regular files, links to external
web pages as well as Canvas 'Pages' (HTML pages) representing assignments etc. may be downloaded. In addition, CanvasSync
may download Canvas assignments along with all linked files that can be found in the description of the assignment. Both
files stored on Canvas as well as external files will be detected.
Lastly, all files that do not fall into the above categories are downloaded and stored in the 'Various Files' folder.

The user may specify various settings including:
- What type of items to be synchronized (files, HTML pages, external links)
- If assignments should be synchronized
- If CanvasSync should attempt to find external files described in the assignment description

Installation
-------------
The easiest way to install and run CanvasSync is by using PIP. Download and install CanvasSync along with its
dependencies (see below) by running:

```
pip install CanvasSync
```

Alternatively, download the source distribution from the https://github.com/perslev/CanvasSync/tree/master/dist on GitHub
(.tar.gz for UNIX and .zip for Windows) and run the following command on the distribution file:

```
pip install CanvasSync-<VERSION>.tar.gz
```

Lastly, you may use the supplied setup.py file to create your own source package or built package for your system.

If you choose not to work with PIP, CanvasSync has the following dependencies that must be installed:

Dependencies
---------------
- Requests  (http://docs.python-requests.org/en/master/)
- six (https://pypi.python.org/pypi/six)

Usage examples
--------------
After installation CanvasSync is launched by executing the following command in the console:

```
canvas
```

When launched without commandline arguments, CanvasSync will start synchronizing with previously specified settings or
prompt the user to enter new settings if no previous settings could be found.

Command line arguments:
-i or --info will display the currently saved settings
-s or --setup will prompt the user to reinitialize settings
-h or --help will show the help screen
-S or --sync to synchronize

Setup
----------
CanvasSync uses the Canvas LMS API (https://canvas.instructure.com/doc/api/) to pull resources on the Canvas server. In
order to authenticate with the server an authentication token must be generated on the Canvas web server. This is done by
going to the 'Account' section followed by 'Settings'. Near the bottom under the 'Approved integrations' section, a new authentication
token may be generated. A token is a substitution to the familiar username-password based authentication and allows
3rd party applications such as CanvasSync to authenticate with the Canvas server API and pull resources. Please note that
by supplying an authentication token to the CanvasSync software, you allow CanvasSync to communicate with the Canvas server on
your behalf, see Disclaimer below.

The process of generating a token is illustrated below:

![](resources/auth_token.png)

The authentication token is stored in a local plain text file in your home directory. Please ensure that your system
has appropriate file permissions to protect this file from unauthorized access.

Disclaimer
----------
Please note that by using CanvasSync the user allows the software to authenticate with the Canvas server on the users
behalf. CanvasSync stores the authentication key locally and the key is never shared with 3rd parties.
The official version of CanvasSync will only pull resources from the server and never remove or modify resources on the
server. Modified/rogue versions of the software could however use the authentication token to remove or modify
resources that the user has access to on the server on the users behalf.

Security note: The authentication token is now stored in plain text format. Please ensure your system is secure and 
consider the risks if others have access to your computer. It is the users responsibility to ensure that the 
authentication token is kept secure.

CanvasSync is still in its early version and is not guaranteed to be stable.

Use this software on your own risk :-)


Additional resources
--------------------
https://www.instructure.com
https://canvas.instructure.com/doc/api/index.html
