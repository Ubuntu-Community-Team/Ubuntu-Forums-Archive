---
title: "is resizing a partition safe?"
date: 2010-08-04
forum: General Help
---

### Post by rockager on 2010-08-04
are there any bad effects of resizing a partition?
(like loss of data).

---

### Post by trentscott on 2010-08-04
Anytime you mess with a partition you're susceptible to data loss -- I'd make sure to have a backup before proceeding. Which partition are you looking to resize?

---

### Post by drs305 on 2010-08-04
There is always some risk, but today's resizing tools generally do a very good job. In Linux, gparted is an excellent tool.

Before resizing, make sure to back up any data you can't afford to lose (to another partition, obviously; a different disk would be even better).

If you want to resize a Windows partition, use Windows software. Although gparted can resize ntfs partitions, using an app designed for Windows is probably safer. And defrag the Windows partition several times before performing any partitioning operations.

Resizing in linux must be done on umounted partitions, so using the LiveCD is a good place to start.

For some tips on resizing, see the second half of the first post in this thread:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by rockager on 2010-08-04
i've made a different partition for the \usr directory which i want to resize. it is ext2.

---

### Post by gadolinio on 2010-08-04
> **drs305 said:**
> there is always some risk, but today's resizing tools generally do a very good job. In linux, gparted is an excellent tool.

Before resizing, make sure to back up any data you can't afford to lose (to another partition, obviously; a different disk would be even better).

If you want to resize a windows partition, use windows software. Although gparted can resize ntfs partitions, using an app designed for windows is probably safer. And defrag the windows partition several times before performing any partitioning operations.

Resizing in linux must be done on umounted partitions, so using the livecd is a good place to start.


+1

---

### Post by adgaps on 2010-08-04
resizing shouldn't really get messed up if you know what you're doing...

when you're shrinking a partition, always remember that what should be left must be larger than the current used space for that partition... if not, your files will most likely be affected, and that'll be a sure disaster if you didn't do some backup beforehand...

personally, i haven't used gparted yet... when i resized my hard drive partitions, i did so with windows 7... then i installed ubuntu in one of the new partitions i created...

---

### Post by FahadMKS on 2010-08-04
I would recommend not to make any changes to the \boot partition and if you really need to make any, make a backup and then try with the partition tools.

---

