---
title: "After 2.6.35-25-generic update, no ethernet, then hard freezes"
date: 2011-01-16
forum: General Help
---

### Post by dugh on 2011-01-16
I updated to the 2.6.35-25 kernel, rebooted, seemed fine.  But then I noticed I had no ethernet connection anymore.  Couldn't get wireless working either.

Then everytime I rebooted, after I would login and start up a browser or whatever, the computer would crash hard, showing the shutdown logo screen, frozen.

Got an Asus n61jv running 64 bit ubuntu 10.10.

Booted back to 2.6.35-24 and it is back to what it was like before.

---

### Post by dugh on 2011-01-17
I haven't found a solution, but I have found that others are having related serious problems with the 2.6.35-25 kernel:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703553](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703553)

---

### Post by cor2y on 2011-01-26
Had this same problem today, the solution is to clear CMOS of your motherboard ethernet  should come back after that in all kernel versions.

---

