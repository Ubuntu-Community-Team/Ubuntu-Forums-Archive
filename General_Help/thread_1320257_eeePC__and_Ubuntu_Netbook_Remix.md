---
title: "eeePC  and Ubuntu Netbook Remix"
date: 2009-11-09
forum: General Help
---

### Post by Martin_sensei on 2009-11-09
Hello,

Has Anyone managed to get the stock ubuntu netbook remix 9.04 to work with an eeePC (mine is a 900 series)?

I managed to install it, but the mouse is really slow and jumpy, it feels like the CPU is really struggling!  There doesn't appear to be any relevant restricted drivers available.

I also tried UNR 9.10 which installed, but never actually loads, it just gets stuck with a desktop and mouse but nothing else.

---

### Post by Martin_sensei on 2009-11-09
Potential fix to (my own) problem :-)

[http://ubuntuforums.org/showthread.php?t=1285598]("http://ubuntuforums.org/showthread.php?t=1285598")

I'll run updates and see what happens...  

Can anyone confirm the performance improves after an update?

---

### Post by coffeecat on 2009-11-09
There was a specially compiled 2.6.28-11 kernel available as a download from a 3rd party site which fixed this issue. I don't have the link anymore but that doesn't matter because the latest kernel upgrade fixed the problem. In fact, iirc, this was fixed by the time of the 2.6.28-14 kernel

Run update-manager and install upgrades. The latest kernel is 2.6.28-16. Reboot and you should be OK.

---

