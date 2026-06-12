---
title: "mkfs.ext4 hans on all disks"
date: 2010-11-26
forum: General Help
---

### Post by fonzie2k on 2010-11-26
Im in a quite stressed situation here,

Im running ubuntu server on a c2d 3ghz server, but got stuck yesterday when i was going to install some new harddrives. 

I did experience some problems during installation of ubuntu as well. 
Tried with an SpinPoint 1TB disk, but the install hanged when ive configured partiotion setup and was writing changes to disk.

However, it worked with a 400gb disk i found under the bed... 

Now im trying to partiotion, format and mount 2x brand new 2TB WD Caviar disks.
Im creating the partition in fdisk, and everything is going well, so far.

But when im trying to format the partitions ive made (sudo mkfs.ext4 /dev/sdb1), everything just hangs.

It just stops right after it start writing.

This is what i get: "Writing inode tables:    60/14905"

And after several tries and 15 minutes waiting time, i get: 

ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir



Ive been googling for hours, without luck :(
Any experteese is greatly appreciated.

---

### Post by fonzie2k on 2010-11-26
Bump

---

### Post by ezsit on 2010-11-26
Try using ext3 and see if you get an error. I'd stay away from ext4 since every so often some one complains of something in ext4 that just works in ext3.

Also, don't bump in under 24 hours - that is the general rule.

---

