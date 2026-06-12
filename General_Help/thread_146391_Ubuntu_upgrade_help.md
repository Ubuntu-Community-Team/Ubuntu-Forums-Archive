---
title: "Ubuntu upgrade help"
date: 2006-03-18
forum: General Help
---

### Post by thetno on 2006-03-18
i enabled Dapper repositories and i did apt-get dist-upgrade after updating.
and now i can't start x anymore. please help the noobie.
I had xgl installed and it was working fine.  
now cat /etc/*release reads shows Dapper and no longer Breezy.
xorg version is now 7 too

---

### Post by Xian on 2006-03-18
You'll probably need more information to troubleshoot this. 
Review your /var/log/Xorg.0.log for error outputs.

---

### Post by thetno on 2006-03-18
it hang with black screen after loading all the modules at startup.
just before it shows the log in screen.
screen resolution seems to have changed, (monitor responded) but it is a black screen
i booted into recovery mode and when i do /etc/init.d/gdm restart
i got the same problem
i have already removed the xgl stuffs from /etc/gdm/gdm.conf 

This is log from /var/log/gdm/:0.log

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux ubuntu 2.6.15-18-386 #1 PREEMPT Thu Mar 9 14:41:49 UTC 2006 i686
Build Date: 21 December 2005
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 18 21:44:17 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:2:0:1) found
error opening security policy file /etc/xserver/SecurityPolicy

```

/var/log/Xorg.0.log doesn't show any error
help

edit: i'm using ati radeon 9600pro.  the apt-get dist-upgrade seems to updated my driver from 8.22.* to 8.23.* too

---

