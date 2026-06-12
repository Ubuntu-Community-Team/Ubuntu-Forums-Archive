---
title: "Access zfs file system (=Solaris) mounted hard drives? Autodetection?"
date: 2010-11-03
forum: General Help
---

### Post by pstein on 2010-11-03
Assume I have an external hard disc which is formatted by a non-ext2/ext3 file system like "zfs" (=Solaris).
 
Can I mount this in Ubuntu as well?
 
in other words: Does Ubuntu have other file system drivers built-in as well or do I have to install appropriate drivers at first?
 
Which file systems in detail (e.g. ReiserFS) are recognized by Ubuntu out-of-the-box?
 
Assume I don't know the new file system. Can I somehow tell Ubuntu: "Look at this device and try to find out which file system is on it?". Or do I have to know the new file system always in advance?
 
Peter

---

### Post by pstein on 2010-12-14
...no answer?

---

### Post by LittleLebowski on 2011-02-14
Using the package zfs-fuse in Synaptic, I have been able to successfully mount and read zfs pools.  Install that and start poking around, I should be able to help some.

---

