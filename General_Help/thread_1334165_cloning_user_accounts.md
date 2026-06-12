---
title: "cloning user accounts"
date: 2009-11-22
forum: General Help
---

### Post by Doug Adams on 2009-11-22
I've set up a very limited user account user "stl" for eight users to access e-mail and 14 websites, I'm clearly having problems with one of the users and have been asked to give each user a separate account so that we can identify the users with problems.
It will take ages to set up all the accounts from scratch to have exactly the same permissions etc. is there a way I can clone the stl account?
I've tried:
 
1, copying files while in main user: will not allow paste  
2, copying files while in root: will not allow paste.
3, using terminal with following in main user and root:
            sudo bash
            cd /home/stl
            tar cf - . | (cd ../gemma;tar xf -)
            chown -R gemma:gemma /home/gemma
            exit
it runs but permission is refused for each file/command.

i'm using 9.04
9.10 crashes so have had to go back to 9.04
all ideas welcome

Doug:confused:

---

### Post by john newbuntu on 2009-11-22
As a root, first create each of the users using the "adduser" command. (Decide on whether they need to be in the same group or not)

Make sure that their entries in /etc/group, /etc/shadow and /etc/passwd files appear the same except the obvious uid, gid and home dirs.

Do a regular "cp" to copy the files (with the -r and -p options, i.e recursive and keep permissions) files from the master user to the other users. Ensure the hidden files are copied too.

Follow it up with a chown and/or chgrp commands to fix permissions.

That should be it mostly.  Now, you may have hard-coded user and/or group names/ids in some of the config files which needs to go through a sed/awk command for cleanup.

---

### Post by Doug Adams on 2009-11-22
> **john newbuntu said:**
> As a root, first create each of the users using the "adduser" command. (Decide on whether they need to be in the same group or not)

Make sure that their entries in /etc/group, /etc/shadow and /etc/passwd files appear the same except the obvious uid, gid and home dirs.

Do a regular "cp" to copy the files (with the -r and -p options, i.e recursive and keep permissions) files from the master user to the other users. Ensure the hidden files are copied too.

Follow it up with a chown and/or chgrp commands to fix permissions.

That should be it mostly.  Now, you may have hard-coded user and/or group names/ids in some of the config files which needs to go through a sed/awk command for cleanup.

Thanks john 

Doug

---

