---
title: "weird problems with either video drivers or xorg"
date: 2011-12-15
forum: General Help
---

### Post by kotoro on 2011-12-15
It seems to be related to 3d rendering. I tried to play heroes of newerth, result: 100% cpu use by xorg, everything else slowed to a crawl. I tried to play minecraft, after a few minutes: same thing occurs, so it doesn't appear to be a game-specific bug. Both of these games worked previously on this system when it was running redhat.

I'm running Ubuntu 11.10 server with ubuntu-desktop installed for the gui and nvidia current for video driver. What can I do to diagnose and fix this?


System is HP workstation xw8600. Was running redhat workstation. Is ubuntu server innappropriate? Should I be using Desktop edition?

System is 64 bit, and thus the OS version I installed was too.

---

### Post by thaelim on 2011-12-16
There's no strong reason why you can't use the server version for this, although the server kernel focuses on different types of workloads so you probably would get better results switching to the desktop version.

What is the type of graphics card listed on the information page in nvidia-settings?

---

### Post by kotoro on 2011-12-19
Quadro NVS 290. When I was running Red Hat on this system it ran the applications I am currently experiencing issues with smoothly at high graphics settings, so something must be amiss at the software level.


System is an HP xw8600

---

