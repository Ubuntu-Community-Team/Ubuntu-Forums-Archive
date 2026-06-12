---
title: "problems with nvidia driver"
date: 2006-04-27
forum: General Help
---

### Post by nicola76b on 2006-04-27
hi all
first of all sorry for english.. i have a sony vaio vgn fe-11h with a geForce go 7400 and i see that finally nvidia support create driver for linux..
So:
1) I download NVIDIA-Linux-x86-1.0-8756-pkg1.run
2) start tty
3) stop gdm
4) install driver
5) modify xorg
6) restart gdm
AND ALL SEEMS OK

but when i restart my laptop xserver dont work (i report error..):

----------------------------
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux boda-laptop 2.6.15-20-686 #1 SMP PREEMPT Tue Apr 4 18:37:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 21 23:24:43 2006
(==) Using config file: "/etc/X11/xorg.conf"
Error: API mismatch: the NVIDIA kernel module has the version 1.0-7174, but
this X module has the version 1.0-8756.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
----------------------------

Any solution?!?!?!? I think that i have to downgrade xorg, but i alway use apt/synaptic and i don't know how...
Thank to anyone

     Nicola

---

### Post by MartinG on 2006-04-27
You don't need to downgrade X, but you do need to remove the older nvidia stuff.  See:
[http://www.ubuntuforums.org/showthread.php?t=103030](http://www.ubuntuforums.org/showthread.php?t=103030)
[http://www.ubuntuforums.org/showthread.php?t=105097](http://www.ubuntuforums.org/showthread.php?t=105097)

The driver numbers have changed but the plan of action is the same.

---

