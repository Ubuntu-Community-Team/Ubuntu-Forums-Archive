---
title: "Sometimes on resume from suspend mode my system is unresponsive"
date: 2010-12-20
forum: General Help
---

### Post by gumkins on 2010-12-20
Hi All,

I have 10.04 64-bit installed on my HP Compaq 6730s laptop.
There is 4Gb of RAM and there is no swap.

I often use suspend to RAM function as it is very suitable for me.
But sometimes when I'm trying to resume HDD led is shining and the system is almost down.
I could not login X session, but in 10-20 minutes (due to system reaction time delay) it is possible to login terminal session (ctrl+alt+F6).
After getting access to console I ran
```
pidstat -d 1 5
```
The command showed me that almost all running in system processes (Skype, Chrome, Firefox, npviewer.bin, apt-get, top, gnome-terminal etc etc...) were reading something.
After several processes killing the system returns to life. BTW, when running that command on normally working system there could be zero process reading something.

It is interesting to me why that happens after resume and why it happens sometimes.
Does anybody have an idea what could be a reason of that?

I don't think that it is normal for swapless system.

Thank you in advance.

---

### Post by gumkins on 2010-12-27
Does anybody have any idea?

---

