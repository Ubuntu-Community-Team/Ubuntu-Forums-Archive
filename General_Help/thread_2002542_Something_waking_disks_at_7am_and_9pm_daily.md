---
title: "Something waking disks at 7am and 9pm daily"
date: 2012-06-12
forum: General Help
---

### Post by alowva on 2012-06-12
I use Ubuntu 11.10 on a headless system, I have two WD Caviar Green drives set up in RAID0 that store only files (videos, music, documents, etc) and use samba to access it over the network.
Hdparm is setup to set the disks to sleep after 10 minutes of inactivity.

Onto the problem:
After a using the system for a while I noticed the disks spun up randomly (I can hear them) when I wasn't accessing data. I setup a simple script that logs when the disk is active, using hdparm -C.
_The disks spin up at around 7am and 9pm everyday and I cant figure out what is doing this..._
I used iotop to check what is accessing files and it seems its something in cron daily, /etc/cron.daily/ contains; apport, cracklib-runtime, man-db, .placeholder, apt, dpkg, mdadm, popularity-contest, aptitude, lighttpd, mlocate, samba, bsdmainutils, logrotate, passwd, standard.

I cant figure out what is spinning the disks up, can anyone help?

Thanks in advance.

iotop log from around that time (removed useless data)...
```
06:39:25 17899 be/4 root        0.00 B/s    3.81 K/s  0.00 %  0.00 % run-parts --report /etc/cron.daily
06:39:26 18607 idle root     1582.38 K/s  309.60 K/s  0.00 % 27.63 % updatedb.mlocate
06:39:34 18607 idle root      251.69 K/s    3.87 K/s  0.00 % 99.99 % updatedb.mlocate
06:39:40 18607 idle root      131.67 K/s    3.87 K/s  0.00 % 99.99 % updatedb.mlocate
06:39:41 18607 idle root        3.76 M/s  684.67 K/s  0.00 % 79.92 % updatedb.mlocate
06:39:42 18607 idle root        6.37 M/s  344.16 K/s  0.00 % 82.42 % updatedb.mlocate
06:39:49   780 be/3 root        0.00 B/s    3.83 K/s  0.00 % 53.75 % [jbd2/md0-8]
```

---

### Post by lordadi on 2012-06-12
It looks like updatedb is running to update the locate index (so that when you type locate, it can find things without actually having to look for them).

There is some more information [here]("http://linux.die.net/man/8/updatedb").

---

### Post by alowva on 2012-06-18
> **lordadi said:**
> It looks like updatedb is running to update the locate index (so that when you type locate, it can find things without actually having to look for them).

There is some more information [here]("http://linux.die.net/man/8/updatedb").

I have tried running each of the scripts in /etc/cron.daily and none of them spin the disks up, i have also tried running "test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )" and again the disks do not spin up.

I have commented out the cron.daily in /etc/crontab for now to see if that makes a difference, but im sceptical.

Do you know of any programs that log what is accessing certain disks? or can iotop do this?

---

### Post by alowva on 2012-06-23
*please excuse the double post, as no one has replied and I have an update.*

Commenting out the line of cron daily in cron tab has stopped the disks being spun up at 6am but they are still spinning up at 9pm!

also now for some reason they are now spinning up at around 4pm as well, seems to be every half hour until 5:30 ish.

as I asked in the earlier post does anyone know of **any tools that would allow me to log what is accessing the disks?**

---

