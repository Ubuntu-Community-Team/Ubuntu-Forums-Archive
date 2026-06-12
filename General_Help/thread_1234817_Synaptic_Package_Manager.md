---
title: "Synaptic Package Manager"
date: 2009-08-08
forum: General Help
---

### Post by lotusalive on 2009-08-08
OMG...  I cannot access Synaptic Package Manager suddenly after several 

Restarts, with Error Msg: Failed to run /user/sbin/synaptic as user root.  

Unable to copy the user's Xauthorization file.  (I must have uninstalled 

something important by accident...)


Will anyone please offer any commands to fix ?  I DO have root access, and 

it DOES recognize Synaptic is installed with the latest version...

help !:confused:

---

### Post by lswb on 2009-08-08
Open a terminal and issue this command 
ls -l .Xauthority

Typical output will be something like
-rw------- 1 user user   117 2009-08-08 09:22 .Xauthority

If you seen anything but your username for the owner and group, where "user user" is shown in the above sample line, delete the file.

$ rm .Xauthority

then logout of the desktop and log back in again, or reboot.

---

### Post by lotusalive on 2009-08-08
Yay, that worked !  Don't know how I DID such a thing ?  Wish I did know, for future reference !  Maybe I'll get time to read up soon, lol ...

Thanks so much lswb, REALLY !:D:popcorn:

---

### Post by lswb on 2009-08-08
Usually that is caused by somehow running as root while using your regular user home directory config files. If you are using the command line to run a gui program as root, use "gksudo program" instead of "sudo program" and this may help avoid it happening again.

---

### Post by lotusalive on 2009-08-12
This has happened AGAIN, now and the terminal is not recognizing the initial command: -l .Xauthority, as 'command not found.' 

Suggestions are appreciated.

Through no doing of my own, I got in to Synatics anyway, without the command, strangely.

System is behaving oddly, just an f.y.i...

---

