---
title: "Booting ubuntu problem"
date: 2010-09-07
forum: General Help
---

### Post by srihari2009 on 2010-09-07
Hi !

ubuntu was booting fine till yesterday , have been using it for about 7 months now on my Dell studio 15" . 

all of a sudden once I shut down and tried to restart it , it's not booting . It says 

"
could not open file system .Maintenance shell opened . Press Ctrl+D to quit the shell and retry "

and shows root@srinath : ~#  and waits for my command have tried to set it right ..and am unable to do so.

Also the same thing happens when I try to boot using recovery mode . Am using ubuntu 9.04

---

### Post by srihari2009 on 2010-09-07
Somebody please help . I have all important information for my project stored on ubuntu and am unable to access it.

---

### Post by garvinrick4 on 2010-09-07
Put in your install cd and boot off of it choose to try Ubuntu not install it. When the CD boots up you open a terminal and try this code.

sudo fdisk -l (lower case L)

find which one is your install such as sda1 or sda5 which ever one that it is.
Lets say it is sda5
```
sudo e2fsck /dev/sda5
``` (use which ever sdaX yours is. X being your #

This just runs a check on file system. 
reboot and see if you are working.
Let us know here what results are.

---

