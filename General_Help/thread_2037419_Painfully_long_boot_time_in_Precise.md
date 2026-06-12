---
title: "Painfully long boot time in Precise"
date: 2012-08-04
forum: General Help
---

### Post by vaul on 2012-08-04
I have made a clean install of Precise Pangolin on my desktop PC shortly after it was released in April and at some point after that I have started to experience an issue with the boot time being astounding 150 (sic!) seconds; in Oneiric the boot time was around ten seconds plus another ten GRUB waited before booting Ubuntu.

Visually, boot process seems go normally, though a BIOS logo stays on the screen for unusually long time — ten seconds (it simply flashed for half a second before) and after the GRUB selects the OS to load it stumbles on a blank purple screen for about one minute.

It is apparently worth mentioning that a ~/ on my filesystem is encrypted, but as far as I can tell from the logs nothing criminal is happening with either eCryptfs or other processes.

_[Here]("http://i.minus.com/ignpYJS4RtAR8.png")_ is the graphic bootchart log and  _[Xorg.0.log]("http://paste.ubuntu.com/1129046/")_, _[auth.log]("http://paste.ubuntu.com/1129049/")_ and a _[syslog]("http://paste.ubuntu.com/1129051/")_ as they appear in the Log File Viewer for the last boot.

Any commentary on the situation, please — do you think it is hardware os software related, where to look?

---

### Post by oldfred on 2012-08-04
You have this throughout your entire log with long time gaps before it posts.

SRST failed (errno=-16)

Quick google search showed some older systems with hard drive connection issues. Are you using IDE/PATA or SATA?

Some did change system and that seemed to solve issue. One had the issue from resuming from suspend?

Does hard drive show Smart Status ok in Disk Utility? Did you add any other devices, CDs, DVDs or change connections?

---

### Post by vaul on 2012-08-04
I have ran short SMART test from the Disk Utility just now and it says that my disk is "healthy" and Disk Utility identifies my drive as Parallel ATA. I did not physcially change anything inside my PC during that clean install, however my DVD drive has stopped working at some point before this issue arised. 

May these issues be connected?

---

### Post by oldfred on 2012-08-04
When I looked in google it was all over the place as far as solutions or issues were. I can only suggest looking and seeing if any apply. 

Others may have a better solution.

Also are you using the blue-tooth? I find anything I am not really using is best turned off or not loaded.

---

