---
title: "gcin: CTRL+space doesn't change input method"
date: 2009-12-24
forum: General Help
---

### Post by curryford on 2009-12-24
recently installed ubuntu 9.10 and upgraded packages

afterwards installed gcin using the following:
sudo apt-get remove 
sudo apt-get install gcin 
im-switch -s gcin

i don't think gcin started automatically, so i probably rebooted and i was able to toggle between the different input methods and type chinese characters in various apps... no problems.

after the next reboot, i couldn't use CTRL+space to change the input method. gcin had started (i see the icon in the tray), and i could click on the icon to change between traditional/simplified, view preferences, etc. i don't recall making any significant changes that might have affected gcin.

i tried restarting gcin, running im-switch... no change. i added traditional chinese font support via system->language support. system->lang support shows gcin as "keyboard input method system". I added export LC_CTYPE=en_US.UTF-8 to /etc/profile. none of this worked. 

i re-installed gcin (via system pkg manager and command line), but the toggling will not work. in gcin settings, "toggle input window" is set to ctrl+space; changed to ****+space for kicks, but still doesn't work.        

_other details:_
XMODIFIERS=@im=gcin
gcin-qt-3-immodule is installed with gcin via synaptic pkg mgr and sudo-apt.

tiger@tiger-desktop:/etc$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/tiger/.xinput.d/en_US" is defined as a link pointing to
ibus
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to default
default - priority 10
default-xim - priority 0
gcin - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim gcin ibus none th-xim 
=======================================================

please don't suggest using SCIM; i prefer to use gcin
thanks

---

### Post by curryford on 2009-12-24
i was dorking around with this some more... issued a "sudo killall gcin" to try manually starting gcin (didn't really work since it restarts on its own)
however, after issuing the killall i can toggle to chinese... [FONT=DejaVu Sans]&#22909;&#22855;&#24618;&#65281;[/FONT]


[FONT=DejaVu Sans]i rebooted the system, but it will only work after the killall. what is interesting is that restarting the gcin service through the gcin tray preferences won't work.
[/FONT]


   	 	 	 	 	 	  so, i am guessing it is an environment issue... not exactly sure how gcin gets automatically started. it doesn't appear to be in /etc/init.d, so i guess via X or gnome which i don't know much about... anyways if anyone has any ideas on any of the above i would appreciate it.

at least i have an easy enough work around. i'll dork around with it more when i have more time to burn :roll:

---

### Post by Taiwan on 2010-01-23
Hey, I have the same problem, and your method (sudo killall gcin) works for me, too. That's very weird. 

I wonder whether such problem has something to do with 64-bit edition. Though my desktop computer, which is 64-bit, has the same problem like yours, I use 32-bit ubuntu on my laptop and have no troubles with gcin.

Does anyone has any ideas? Thanks for reading.

---

### Post by king smith on 2010-01-23
Does the permittivity of free space or vacuum is the highest permittivity of a medium or the least? And also how does it change?

---

### Post by momonextby on 2010-03-26
The same here, have to "killall gcin" to make it work.

---

