---
title: "What and where is the config file that determines the commands to do on bootup."
date: 2010-03-31
forum: General Help
---

### Post by robofighter on 2010-03-31
I am using Ubuntu server 9.10.

Also for shutdown and restart too.

---

### Post by blueridgedog on 2010-03-31
For start up, I have copied a prior post:

1. When booting all commands in /ect/init.d/rc.local are run. This file also calls and runs /etc/rc.local. These are the equivalent to the DOS autoexec.bat file system, but if you are under 30, you don't know what that it is and it seems like silly reference.

2. In /etc you will find various directories named /ect/rcn.d where n is a number from 0 to 6. These numbers represent the different Linux run levels. The default Ubuntu run level is 2, so if you look inside /etc/rc2.d you will see symbolic links back to files in /etc/init.d. Files with a capital S are run when the system starts to that run level, others are not. Note that Ubuntu/Debian defaults to run level 2 and uses a GUI at that point which is contrary to most Linux configurations.

3. The window manager also starts applications when the user logs in, running these applications as the user, not as system level applications. The gnome applications you configure to run at start are setup as files in the directory /home/USER/.config/autostart. Gnome applications also start based upon the entries in /etc/xdg/autostart/ and if you use the gui to disable them, a negating entry is placed in your /home/USER/.config/autostart directory.

4. Applications can be started via entries in the files /home/USER/.bashrc and /home/USER/.bash_profile.

5. A script called "Default" can be placed in /etc/gdm/PostLogin, /etc/gdm/PostSession and /etc/gdm/PreSession. The sripts will be run as root at the time implied by thier directory name. (note the capitals in the file names and path names)

When shutting down, all files in /etc/rc0.d are run, there are other shutdown processes, but I have never had a good reason to investigate them.

---

### Post by geirha on 2010-03-31
This is controlled by upstart. See the explanation of The Init Process at [https://help.ubuntu.com/community/KnowThyUbuntu](https://help.ubuntu.com/community/KnowThyUbuntu).

And the external links at [http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart) has some useful information.

---

### Post by t4thfavor on 2010-03-31
You can also run commands using CRON, and specifying the Reboot flag. You'll have to find out what flag that is, cause I can't remember..

---

