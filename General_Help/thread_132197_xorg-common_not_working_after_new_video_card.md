---
title: "xorg-common not working after new video card"
date: 2006-02-17
forum: General Help
---

### Post by Ben Stamper on 2006-02-17
After installing an eVGA nVidia 5500 FX to a computer(Running 5.10) that previously had been running fine off of on-board memory, xorg-common has been giving this error:
> 
(EE) No Device Detected

Fatal Server Error
No Screens Found


I've attempted running 'sudo dpkg-reconfigure xorg-common', which runs, but still doesn't correct the issue. The computer runs fine off of a 5.04 Live Disk. Thank you for helping, I'd like to fix this as quickly as possible.

---

### Post by Ben Stamper on 2006-02-18
I've reconfigured the xserver-xorg(using 'sudo dpkg-reconfigure xserver-xorg', which brings up a somewhat graphical configuration tool), but now Ubuntu freezes at the login screen( there is a portion of the login screen that is plain white, not loaded).

---

### Post by Ben Stamper on 2006-02-18
Hmm, I just remembered that I used the nVidia drivers instead of the open-source nv. Might this be causing the problem?

---

### Post by nalmeth on 2006-02-18
yeah, set the driver in dpkg-reconfigure xserver-xorg to 'vesa' to see if you can load up the x, and then install new drivers from inside

---

### Post by Ben Stamper on 2006-02-18
Okay, after setting it to use the vesa driver, X works.

---

