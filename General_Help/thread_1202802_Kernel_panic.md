---
title: "Kernel panic"
date: 2009-07-02
forum: General Help
---

### Post by pigreco on 2009-07-02
Hi! I'm new in the forum and I've been using Ubuntu 9.04 for one week in the 64bit flavour. Two days ago I started a heavy process that had been running for nearly one day. Unfortunately after all this long period, the system freezed and I had to reboot the system. The cause of this is to me mysterious, but it seems that the error was something like  "Unable to handle kernel paging request".

I'd like to know if such a problem is caused by hardware or software. Moreover, is it possible to save the status of the machine at a certain point and restart executing all the processes later from that point? This would be greatly useful in case of kernel panic.

---

### Post by quixote on 2009-07-03
What kind of 64-bit system do you have?  And do you have the most recent update?  If you've been using it only for a week, the answer is probably yes, but an earlier version of the kernel (2.6.28.11) caused major problems on some 64-bit systems.  See the [known bugs thread]("http://ubuntuforums.org/showthread.php?t=1145967") (page down a bit).

If you have the critical hardware (ICH8 or ICH9 hard disk controller chip, I believe), and the 28.11 kernel, it's really important to upgrade.  The filesystem corruption can result in data loss.

OTOH, if that's not the hardware you have, there's some other problem, and I'm not sure what it could be.

---

