---
title: "[Gparted] 2GB used after formating ext4"
date: 2010-01-05
forum: General Help
---

### Post by m42h31 on 2010-01-05
[[IMG]http://img130.imageshack.us/img130/1174/gpartedproblem.png[/IMG]]("http://img20.imageshack.us/img20/1174/gpartedproblem.png")
i buy new seagate baracuda 250GB, i split it into 2 partition with ext4 *(hard drive will use for data)*.
why ext4 in gparted use 2GB for each partition?? *please see picture, click the picture for original size.*

---

### Post by wirelessmonkey on 2010-01-05
Because filesystem information is written to the drive, which takes up space. Usually around 2%, depending on which filesystem used.

---

### Post by m42h31 on 2010-01-05
i'm not using this partition for root ("/"). but for Data *(/media/Data1 and /media/Data2)*.
can i escape this used space?? 2 x 2GB is very big size for saving filesystem information.

---

### Post by dcstar on 2010-01-05
> **m42h31 said:**
> i'm not using this partition for root ("/"). but for Data *(/media/Data1 and /media/Data2)*.
can i escape this used space?? 2 x 2GB is very big size for saving filesystem information.

No, if you want all the features of a journaling filesystem you sacrifice a insignificant part of the disk space.

---

### Post by wirelessmonkey on 2010-01-06
If you have a filesystem on a drive, the filesystem will take up space. Not much you can do about that, except pick a different filesystem.

---

### Post by Wollombi on 2010-02-01
> **m42h31 said:**
> i'm not using this partition for root ("/"). but for Data *(/media/Data1 and /media/Data2)*.
can i escape this used space?? 2 x 2GB is very big size for saving filesystem information.

It doesn't matter if it is root or not.  When you create a partition and format it, the partition creates a table that is used to locate data that is/is to be written/deleted.  It takes a little bit of space, and it's normal.

This will happen no matter what filesystem you use, beit ext, ntfs, fat, etc.  There are slight differences in the amount of space each uses, but usually this is a minor detail for choosing a filesystem - more important are things like robustness/reliability, ability to recover "lost" data, cluster size, speed of operation, etc.

---

### Post by underquark on 2010-02-01
Just try it on a 1.5Tb drive and choke at the amount used.

---

