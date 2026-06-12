---
title: "disk space"
date: 2009-09-20
forum: General Help
---

### Post by sandpiper900 on 2009-09-20
I've just downloaded Ubuntu 9.04 desktop
i'm trying to install the latest updates,but i get the message not enough free disk space on disk'/'
How do i free up disk space...by the way this is my first venture into Ubuntu,so i'm totally green
Hope someone can help            ...thanks

---

### Post by P4man on 2009-09-20
Did you do a "wubi" install from windows ? If so, easiest is starting over and give ubuntu some more space than you did the first time.

 If you did a regular install to a dedicated partition, then this guide may help:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by bodyharvester on 2009-09-20
hi

could you open a terminal and type:

code
```
df -h
```

---

### Post by cogier on 2009-09-20
You have not given much detail but I guess you have installed Ubuntu on a machine that has Windows on and unfortunately not enough room has been left for Ubuntu. You can check how much space you have by SYSTEM > ADMINISTRATION > SYSTEM MONITOR then click on the FILE SYSTEM tab.

If this is the case a braver person than I can explain how to repartition disks to sole this. In the short term you could make extra space by going to APPLICATIONS > ADD/REMOVE and un-check software that you do not want and then select APPLY CHANGES.

Then you can try the updates again. SYSTEM > ADMINISTRATION > UPDATE MANAGER.

---

### Post by drs305 on 2009-09-20
sandpiper900, 

Welcome to Ubuntu. When you run the "df -h" command previously mentioned, look to see if your partition is 2.5GB. There is a bug in the "side by side" Step 4 in the installation package. If you don't change things, the default partition will be too small.

Here are a couple of posts that will help you **if that is the problem**:

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

