---
title: "Home partition resized from Windows program"
date: 2012-01-04
forum: General Help
---

### Post by Ellimist on 2012-01-04
Hello,

My configuration :

/ is mapped to /dev/sda2
/home is mapped to /dev/sda6

My cousin today resized /dev/sda6 to create unallocated space using a Windows program called Paragon Hard Disk Manager just because it had the most free space. I cannot access the partition anymore. Trying to fsck fixes a few errors and then yields this error :

> fsck.ext4: e2fsck_read_bitmaps: Illegal bitmap block(s) for /dev/sda6.
e2fsck: abortedI hope the data is still there. I just need to recover the data in some way.

Edit: Apparently, the Windows program doesn't recognise ext4 partitions. It resized the partition as an ext3 partition.

---

### Post by 2F4U on 2012-01-04
You probably have to look for data recovery or rescue software or even professional help. The partition seems to be corrupted, probably because the tool your cousin used does not know how to handle ext4 partitions.

---

### Post by Mark Phelps on 2012-01-04
According to their website, Hard Disk Manger v11 DOES handle Ext4 filesystems.  If the version used was older than this, that could explain the resulting filesystem corruption.

And ... in my own experience, Windows utilities do better handling Windows filesystems and Linux utilities do better handling Linux filesystems.

So next time, tell them to use GParted, not Paragon.

---

