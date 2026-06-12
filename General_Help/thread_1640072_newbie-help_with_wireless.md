---
title: "newbie-help with wireless"
date: 2010-12-07
forum: General Help
---

### Post by tuner1406 on 2010-12-07
hello, i am new to ubuntu, i have never used it before in my life, i just installed 10.10 beta on my laptop, and the wireless isnt working (acting like theres no driver for it) i cant turn it on or off with the button. i have been looking at some other threads and everyone keeps telling people to do these codes and whatnot, could someone tell me how to get my wireless to work and in a way where i can understand it
 
i have a compaq presario c700 with broadcom BCM4311 wireless card

---

### Post by azertyh on 2010-12-07
hello,
read this [howto](http://ubuntuforums.org/showthread.php?t=1604868).
and did you search if you have additional drivers?

---

### Post by tuner1406 on 2010-12-07
i did that how to, and nothing came up in the search, how do i search for additional drivers?

---

### Post by gobbles414 on 2010-12-07
Beta versions of Ubuntu are UNFINISHED, provided to the community for testing so that there will be less bugs in the final release. In other words, your problem may be a bug in the beta version that was solved in the final release. Also, despite what others might tell you, upgrading from the beta version to the final release will NOT provide as satisfactory a result as a "fresh install" of the final release.

Therefore, my first recommendation is that you obtain a final release copy of 32-bit Ubuntu 10.10 (some software/drivers not available yet in 64-bit version). Backup all of your files, and do a "fresh install" of the final release version.

After installing the final release version, go System => Preferences => Network Connections, and tell us about anything in there that looks like it is about wireless.

---

### Post by TBABill on 2010-12-07
Easiest to try first is to plug into a router since you are on a laptop (via ethernet cord). Then click SYSTEM>>ADMINISTRATION>>ADDITIONAL DRIVERS. Most likely you will be prompted to install either the B43 or STA driver for a Broadcom card. The text box will tell you which models are supported by each. I believe the 4311 uses the STA driver and it seems most reliable if it supports your card. Just click activate and it will download the driver and install. Then reboot.

---

### Post by Sef on 2010-12-07
> i have a compaq presario c700 with broadcom BCM4311 wireless card

Common problem, so don't feel too frustrated about it. You need to download some [firmware]("http://ubuntuforums.org/showthread.php?t=1604868").

---

