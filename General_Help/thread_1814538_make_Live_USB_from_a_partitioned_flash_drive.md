---
title: "make Live USB from a partitioned flash drive?"
date: 2011-07-29
forum: General Help
---

### Post by u-noob-tu on 2011-07-29
i bought an 8gb flash drive this morning that i was on sale for almost the same price as a 2gb drive. i want to set it up to have 2.5gb for turning into a startup disk and the rest for miscellaneous stuff. i used gparted to set up the partitions with no problem. when i go to startup disk creator, neither partition is found, even though they are both mounted. is it possible to set up a flash drive this way?

---

### Post by C.S.Cameron on 2011-07-29
If you want to also use it as a data disk for Windows, remember that Windows can only see the first partition of a flash drive.
Startup Disk Creator also needs to use the first partition.
So forget multiple partitions, (Unless you don't use Windows), and just make a folder named Data or such.
When booting from the Live drive you can find the data folder in cdrom.
You may need to be root to access it though, so use gksu nautilus.

---

