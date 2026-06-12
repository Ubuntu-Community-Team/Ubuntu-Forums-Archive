---
title: "password protected script"
date: 2011-04-20
forum: General Help
---

### Post by thomas515 on 2011-04-20
I want to password protect a script's code from being viewed in a text editor.  any idea on how to do this?

---

### Post by smurphy_it on 2011-04-20
You could always use gnupg to encrypt the file.  Then un-encrypt it before use.  Not sure if that is of any use to you.

---

### Post by thomas515 on 2011-04-20
What I'm doing is setting up a few scripts to auto-execute sudo tasks (ie: start and stop the GUI, shutdown, etc). What I have now is a script with the password that I'm piping to the script to execute the command.  I want to protect the password file to keep someone from being able to view it and then get the password.  I know this isn't secure but I'm just trying stuff out

---

### Post by perspectoff on 2011-04-20
Here's two suggestions:

1) ---------------------------

Create a new user account to be used for scripts. Give that user sudo privileges so it can execute the scripts.

Create a folder in which you will store your scripts. Encrypt the folder and only give the newly-created user read/write permissions to that folder.

Run the scripts as the user you created.

2) ----------------------------

Also, there used to be a utility shc that turns scripts into binaries (obscuring code and passwords), available from the older Debian repositories:

[http://archive.debian.net/etch/i386/shc](http://archive.debian.net/etch/i386/shc)

You can install it by adding the repository:

 deb [http://archive.debian.org/debian](http://archive.debian.org/debian) etch main

i.e.

 sudo add-apt-repository 'http://archive.debian.org/debian etch main' 

and then installing the shc package:

 sudo apt-get install shc

Obviously, both these steps can be done with a package manager like Synaptic or KPackagekit.

Usage instructions are at:

[http://www.datsi.fi.upm.es/~frosal/sources/shc.html](http://www.datsi.fi.upm.es/~frosal/sources/shc.html)

---

### Post by thomas515 on 2011-04-20
well I password protected the script using vim -x file.  The problem I'm having now is when I boot up for the first time, I have to enter the password for each script.  After that I can run said script without  the password.
heres the GUI start script:

#!/bin/bash
echo ./word | sudo service gdm start

the ./word script is:

#!/bin/bash
echo password
clear

---

### Post by Spyderkid on 2011-04-20
[edit]
never mind this post its irelevant

---

### Post by Spyderkid on 2011-04-20
Just use OpenOffice or LibreOffice instead, then you can save with password

---

