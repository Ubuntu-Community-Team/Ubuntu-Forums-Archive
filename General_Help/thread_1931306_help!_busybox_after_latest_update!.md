---
title: "help! busybox after latest update!"
date: 2012-02-25
forum: General Help
---

### Post by DrScum on 2012-02-25
On a desktop machine running ubuntu 10.04 I just performed the latest update. The update completed with the message your system is up to date. The system was shut down normally. Now at the next restart I get a busybox with the following messages appearing:

.
.
.
Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
mount: mounting /dev on /root/sys failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
[    1.543634] usb 3-2: configuration #1 chosen from 1 choice
No init found. Try passing init= bootarg.


BusyBox v1.13.3. ....

No Idea what to do now!

Help is greatly appreciated

---

### Post by imbrinix on 2012-03-09
[http://ubuntuforums.org/showthread.php?t=1929295&highlight=no+init+found+passing+init+bootarg](http://ubuntuforums.org/showthread.php?t=1929295&highlight=no+init+found+passing+init+bootarg)

I'm having the same problem repeatedly, but this fix works each time.

---

### Post by DrScum on 2012-03-10
Thanks for the reply. I ended up booting with a Puppy Linux CD, saving all important data and installing a new system (Ubuntu 11.1). After a week of on and off and a lot of reading in forums and how tos I was about where I'd been before except with an up to date system. I actually learned a lot, but obviously this is not the way to go if productivity depends on the system to be repaired!

---

