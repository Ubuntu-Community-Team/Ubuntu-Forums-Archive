---
title: "howto backup NTFS files modified after a certain date?"
date: 2010-05-14
forum: General Help
---

### Post by mdgill on 2010-05-14
I clone my entire notebook hdd once a month to a USB drive with an identical disk once a month using dd.  I would like to find a way to automatically or manually do incremental backups at shorter intervals.

The first problem is that my incremental backup drive is not the same as my full backup drive (which is my clone).  Is there some way to backup or copy all files on a document partition modified after a certain date?

The second problem is that my document partition is NTFS-3G.  I guess this could be done pretty easily using "dump" if I stored my docs on ext.  [I don't because I want to make sure that my docs are accessible from any machine (say in an Internet cafe) should my MacBook die and I need to rip out the hard drive and run to do my homework on another system; that is why I keep my docs on my Vista partition].

Any suggestions?

---

### Post by BoneKracker on 2010-05-14
This works well for me:

[http://rsnapshot.org/](http://rsnapshot.org/)


What's amazing about it is what it achieves through use of hard links.

---

