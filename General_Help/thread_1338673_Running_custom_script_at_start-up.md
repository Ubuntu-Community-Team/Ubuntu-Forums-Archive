---
title: "Running custom script at start-up"
date: 2009-11-26
forum: General Help
---

### Post by Xiphias71 on 2009-11-26
Hi, I'm sort of a newbie to Ubuntu, and I've been messing with the power management options and scripts and stuff. I've been trying to run this one script from start up, but for some reason it would not. The 2 ways I tried were:

1) Adding the script to 'Start up Applications'
2) Um...this: [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

And yes, I have made my script as an executable. Neither way worked - I end up having to manually run the script myself after start up. The script consists of some code to optimize the use of battery, and I know it's not working because Powertop shows 38+W consumed, until I run the script manually, which drops it to ~20W.

---

### Post by mo.reina on 2009-11-26
try adding the script name to this startup script

*/etc/gdm/PostLogin/Default*

this script is run after successful login, but before any other settings are configured.  you might have to create the script, there is usually a sample in the same directory called Default.sample

if this doesn't work, try adding the scriptname to the presession script

*/etc/gdm/PreSession/Default*

---

### Post by Xiphias71 on 2009-11-26
Hmm, tried your first method, it isn't working. Should it really be this difficult?

---

### Post by blueridgedog on 2009-11-26
Ways to have things run at "start"

1. When booting all files in /ect/init.d/rc.local are run. This file also calls and runs /etc/rc.local where a user can place custom start items.  These are the equivalent to the DOS autoexec.bat file system, but if you are under 30, you don't know what that it is and it seems like silly reference.

2. In /etc you will find various directories named /ect/rcn.d where n is a number from 0 to 6. These numbers represent the different Linux run levels. The default Ubuntu run level is 2, so if you look inside /etc/rc2.d you will see symbolic links back to files in /etc/init.d. Files with a capital S are run when the system starts to that run level, others are not.  Note that Ubuntu/Debian defaults to run level 2 and uses a GUI at that point which is contrary to most Linux configurations.

3.  The window manager also starts applications when the user logs in, running these applications as the user, not as system level applications. The gnome applications you configure to run at start are setup as files in the directory /home/USER/.config/autostart. Gnome applications also start based upon the entries in /etc/xdg/autostart/ and if you use the gui to disable them, a negating entry is placed in your /home/USER/.config/autostart directory.

4.  Applications can be started via entries in the files /home/USER/.bashrc and /home/USER/.bash_profile.

5.  A script called "Default" can be placed in /etc/gdm/PostLogin, /etc/gdm/PostSession and /etc/gdm/PreSession.  The sripts will be run as root at the time implied by thier directory name. (note the capitals in the file names and path names)

If you have a script that is supposed to run via one of these methods and it seems to not run, you need to build in some debugging so that you can see what is working or failing.  This can include logging, or simply checking logs for errors.  A simple approach is to have the script create a log file of its actions so you at lease know that it was run and can then focus on either figuring out why it is not running or why it is running, but not working.  If you know the script is running, perhaps something else is changing the settings after it runs.

---

### Post by dcstar on 2009-11-27
> **blueridgedog said:**
> Ways to have things run at "start"

1. When booting all files in /ect/init.d/rc.local are run. This is the equivalent to the DOS autoexec.bat file system, but if you are under 30, you don't know what that it is and it seems like silly reference.
........

Rubbish, /etc/init.d/rc.local is a system script that should not be touched in any circumstances.

All it does is execute /etc/rc.local which can contain anything a user wants run at boot time - that file is what is edited if required.

---

### Post by blueridgedog on 2009-11-27
> **dcstar said:**
> 
All it does is execute /etc/rc.local which can contain anything a user wants run at boot time - that file is what is edited if required.

True!  As a recent convert to Ubuntu, I have yet to sort out a few of the file locations from my decades running Red Hat systems (and don't even get me started on network interfaces).

However, you have shown another way for programs to run at start, as it is possible that something could be in either location.  The list isn't so much of a "put your stuff here" as it is a way to understand the many ways something can be initiated at start.

---

