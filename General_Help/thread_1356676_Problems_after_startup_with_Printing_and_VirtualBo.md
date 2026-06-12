---
title: "Problems after startup with Printing and VirtualBox."
date: 2009-12-16
forum: General Help
---

### Post by theicyj on 2009-12-16
After installing updates on Ubuntu 9.10 (32 bit) a week or two ago, I now have to run "sudo service cups start" and "sudo modprobe vboxnetflt" to print or run Virtualbox (3.1), respectively.  After I run "sudo service cups start" then printing works fine until I reboot.  Also, once I run "sudo modprobe vboxnetflt", my virtual machines start perfectly. 

How can I get Ubuntu set up so I don't have to run these two commands at startup?  Up until a week or so ago I did not have to run these cmds, why now?

Thanks!

---

### Post by theicyj on 2009-12-16
UPDATE: I fixed the VirtualBox issue by adding "vboxnetflt" to a new line in the file "/etc/modules".  Now "vboxnetflt" seems to load at boot.

Still unsure why the CUPS service does not start with Ubuntu.  Any ideas?

---

### Post by theicyj on 2009-12-16
When I go to system -> preferences -> default printer, I get the following message:

CUPS server error

The CUPS scheduler is not running.

1. I have tried uninstalling CUPS, then reinstalling.  It still does not start up unless I run the command: 

"sudo service cups start"

2. I have tried adding "sudo service cups start" to /etc/rc.local .  NO LUCK!

ANYONE!?

---

### Post by theicyj on 2009-12-22
Anyone? [-o<  I can't seem to find anything in the logs, then again, I am not sure if I am looking at the right log files...

---

### Post by sovesky on 2009-12-23
Just another "I also have that problem" post. :confused:

---

### Post by evetsat on 2009-12-31
Me too.  No problems with CUPS until now but now I have to manually start CUPS each time.

---

### Post by theicyj on 2010-01-05
Bump! (again)

Seems I am not the only one with this problem!

Why do I need to run "sudo service cups start" to print?  Should the printing server not start up by itself at boot?  As a side note, I have switch two of my three PCs to opensuse 11.2.  I have plans on switching my third, I am sick of things just not working, I have not had a single issue with opensuse besides less apps in the repos.  It is a shame because I have been using Ubuntu since 7.04...

---

### Post by evetsat on 2010-01-09
Seems to be a problem with Upstart.  Suggested solution here:

[http://ubuntuforums.org/showthread.php?t=1305226](http://ubuntuforums.org/showthread.php?t=1305226)

to downgrade Upstart 0.6.3-10 worked for me.

---

### Post by gtr225 on 2010-01-09
Add me to the list of me toos

---

