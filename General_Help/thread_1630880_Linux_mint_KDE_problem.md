---
title: "Linux mint KDE problem"
date: 2010-11-25
forum: General Help
---

### Post by raforon on 2010-11-25
Hi all,
I have recently installed LM9 KDE on my desktop. All had been working fine till yesterday.
I wanted to setup a private folder. There was one already set up, I decided to delete it and make a new one.
I ran the following commands in the terminal as per what I read on ubuntu website
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private 
This command said that the folder was already there, so that is when I decided to delete Private folder and make a new one as I wanted to set up a passphrase for it
Then I ran the following commands
Ensure that you have moved all relevant data out of your ~/Private directory
Unmount your encrypted private directory
 $ ecryptfs-umount-private 
Make ~/Private writable again
 $ chmod 700 ~/Private 
Remove ~/Private, ~/.Private, ~/.ecryptfs (Note: THIS IS VERY PERMANENT)
 $ rm -rf ~/Private ~/.Private ~/.ecryptfs 
Uninstall the utilities
 $ sudo apt-get remove ecryptfs-utils libecryptfs0 

after I ran the final command, dolphin and terminal stopped working. After a restart they worked ok for a few minutes but then got stuck again. another restart and now the system wont boot. It goes to the login screen but on typing password in, it says that some config file not found error code 3, check installation. Sorry I can not remember the exact error code message

Any help would be appreciated.

---

### Post by raforon on 2010-11-27
The error message says "kstartupconfig4 does not exist or fails. The error code is 3. Check your installation"

I tried logging in into fail safe mode, Nothing happens. I just get a black screen which says

"(process:254): Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)". I just have to power the system off at this point.

thanks for your time

---

