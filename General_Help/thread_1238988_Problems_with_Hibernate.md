---
title: "Problems with Hibernate"
date: 2009-08-13
forum: General Help
---

### Post by DrFalken on 2009-08-13
Ok so I had to go eat dinner and I put my computer in hibernate.  The problem was I think it just shut down, and when I turned it back on, there were two versions of linux listed in the boot loader.  I figured it had stored my last session as an image, so I clicked on it and lo and behold it said "waking up...".  Here's where the problems start.  It took me to the usual screen you get after hibernation, but I couldn't type anything at all, so I couldn't log in.  I had to shut it down, but that image isn't gone and I've lost 2 Gigabytes of disk space instantly.  What's wrong and how can I remove that extra image in the boot loader and get back that space on my hard drive?

---

### Post by Yvan300 on 2009-08-13
Hate to burst your bubble here, but from experience, hibernation and ubuntu don't mix. Although i got mines working in jaunty, it was way slower than a normal reboot. So all in all, if you want to start off where you left off, i think there is an option in power management to do that.

Good luck!

---

### Post by P4man on 2009-08-13
first of all, you didn't lose 2GB. When you hibernate, the image is saved to the swap partition (or file). After resuming that swap space becomes swap again, you don't lose it ;).

Secondly the above poster is right. Hibernate is all but useless on ubuntu. It takes forever to hibernate or resume. Its quite possible your machine was resuming normally but you just didn't wait long enough (and i cant blame you lol). Suspend is a lot more useful. It doesnt save your stuff to harddisk, but keeps it all in ram, then shuts the machine down except for the ram. power consumption is close to zero, and it resumes in seconds.

---

