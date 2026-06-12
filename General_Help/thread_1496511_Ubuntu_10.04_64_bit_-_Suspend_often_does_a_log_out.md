---
title: "Ubuntu 10.04 64 bit - Suspend often does a log out"
date: 2010-05-29
forum: General Help
---

### Post by taylorkh on 2010-05-29
This one seems to be a little different from the other "problem with suspend" threads.

Dell Studio XPS 8000 desktop
i7-860 CPU
8 GB RAM
swap area set to 9 GB
nVIdia GeForce GT220 1 GB
Ubuntu 10.04 64 bit, all patches, nVidia-current 195.36.15

I am finding that about 1 out of 5 times when I "suspend" the computer and then power it back on (bring it out of suspend using the power button) I am presented with a login screen and any programs which were running at the time of suspend are terminated. Ubuntu 9.10 on this machine experienced the same problem about 1 in 20 times. Hardly an improvement

Suspend does seem to work in that the power usage by the box drops to almost nothing, fans and hard drives go quiet and the monitors go into power saving mode.  It is the UNsuspend which seems to be my problem.

Any suggestions on how I can diagnose this issue?

TIA,

Ken

---

### Post by taylorkh on 2010-07-03
The issue has been determined to be related to having a virtual machine running at the time of suspend.  No VM running no problem with suspend.

---

