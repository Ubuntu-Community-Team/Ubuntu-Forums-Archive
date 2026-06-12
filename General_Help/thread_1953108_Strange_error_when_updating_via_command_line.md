---
title: "Strange error when updating via command line"
date: 2012-04-05
forum: General Help
---

### Post by HunterDX77M on 2012-04-05
Hey guys, I just tried to update right now and got the following error message:
```

murshed@murshed-Inspiron-1545:~$ sudo apt-get update
[sudo] password for murshed: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
murshed@murshed-Inspiron-1545:~$ 

```

What does this mean? Can anyone help me solve it? I also can't update through Update Manager either (it just hangs up with the message "waiting for apt-get to exit").

---

### Post by chestycuogth on 2012-04-05
this has happened alot to me (and iv'e barely had ubuntu for a month) i'd say it's worth learning to fix this off by heart

A very common error while installing an application or updating a package is following:

E: Could not get lock /var/lib/dpkg/lock &#8211; open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

The reason is quite obvious from the error itself &#8220;another process using it&#8221;. Which means another process is already using the mentioned directory (necessary for the application to be installed) through Synaptic Package Manager, Update Manger, terminal or Ubuntu Software Center.

The idea would be to look for another application which is being installed or update it. Wait for it to finish the installation or cancel it. If you cannot see the application then try running this command in the terminal to solve this error:

> sudo rm /var/lib/apt/lists/lock

[http://maketecheasier.com/fix-ubuntu-update-errors/2011/12/16]("http://maketecheasier.com/fix-ubuntu-update-errors/2011/12/16")

if you get a differant error, then copy and paste the error into google.

EDIT: i just got exactly the same error as you and the solution above did not fix it. if the above does not work then try this
1. sudo rm /var/cache/apt/archives/lock
2. sudo dpkg --configure -a

you may have to repeat step 1 if it doesnt work the first time

---

### Post by HunterDX77M on 2012-04-05
The error went away for now. I just tried the mother of all computer problem fixes, reboot, and it worked.

---

### Post by dcstar on 2012-04-05
> **HunterDX77M said:**
> 
........
What does this mean? Can anyone help me solve it? I also can't update through Update Manager either (it just hangs up with the message "waiting for apt-get to exit").

It usually means that the automated update is running. Wait until it finishes.

---

### Post by chestycuogth on 2012-04-06
> **dcstar said:**
> It usually means that the automated update is running. Wait until it finishes.

iv'e also noticed it happens with certain pieces of software that don't install properly

---

