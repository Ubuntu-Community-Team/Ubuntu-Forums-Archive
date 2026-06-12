---
title: "btrfs fsck error - how to fix it ?"
date: 2012-04-29
forum: General Help
---

### Post by masuch on 2012-04-29
Hi,

I am trying to revover btrfs filesystem after upgrade to ubuntu precise.
I have tried:

$ sudo fsck -r -V -t btrfs /dev/sdb8
fsck from util-linux 2.20.1
[/sbin/fsck.btrfs (1) -- /dev/sdb8] fsck.btrfs -r /dev/sdb8 
root 5 inode 251945 errors 400
root 5 inode 251954 errors 400
found 11405721600 bytes used err is 1
total csum bytes: 10576496
total tree bytes: 557309952
total fs tree bytes: 517558272
btree space waste bytes: 149250982
file data blocks allocated: 25370923008
 referenced 10748383232
Btrfs Btrfs v0.19


$ sudo btrfsck /dev/sdb8
root 5 inode 251945 errors 400
root 5 inode 251954 errors 400
found 11405721600 bytes used err is 1
total csum bytes: 10576496
total tree bytes: 557309952
total fs tree bytes: 517558272
btree space waste bytes: 149250982
file data blocks allocated: 25370923008
 referenced 10748383232
Btrfs Btrfs v0.19


but nothing worked at all.

is there any other way how to fix it ?
I do not mind if some data are going to be lost. some guidance if exists I would much appreciate.

thank you,
kind regards,
M.

---

### Post by The Cog on 2012-04-29
As I understand it, there is no fsck for BTRFS yet. The existing one will tell you there are errors but won't fix them (or even attempt to). So all it can really tell you is that you need to reformat and restore from backup. 

Their argument for not releasing a working fsck is that attempting to fix the filesystem might make it worse, which doesn't make sense to me. What, they might kill it dead again? 

Actually, I am wondering if Oracle are planning to never release a free working fsck at all, but charge a license fee for it.

---

### Post by masuch on 2012-04-29
Hi,

Your suggestion is exactly what I am trying to avoid.
I made backups (tar , rsync)  right before I did dist-upgrade from oneiric to precise but after upgrade I did not get into system because of filesystem errors.
Upgrade took me more than six hours to be done within correcting dependency hell and other distro upgrade failures which always happened within dist-upgrade.
So , you suggesting me to pray when I do dist-upgrade on btrfs again when I recover system from my backup ?
(I have to say - this is something where NTFS is absolute winner. I succeeded in 90 percent hundreds of cases within last 15 years to recover this file system to functional state (even for prize that in many many cases I have lost some files but I did revover only those couple of damaged files) from on xp -> vista to win7 OS 32 or 64 bits platforms)
Does have linux any filesystem with such excelent ability to survive - recover from crashes - damaged files/metadata - I would preferable use it ?
I have been trying to use btrfs for one year (from April) and it is still big troublemaker and seems to me will be still for long time ahead. It seems that it is quite waste of time to pay small attention to btrfs filesystem at all.

---

### Post by maciejus on 2012-04-30
Just to let yo know there is a more recent version of btrfsck in the git repository and that version can do some filesystem fixes. Moreover there are few additional commands such as btrfs_zero_log which can recover from some errors. There is also an issue with dpkg working on btrfs due to some filesystem calls that are in fact duplication of btrfs internal features so I use eatmydata to avoid that and all the upgrades work really fast - just type "eatmydata aptitude" or similar and do the upgrade.

---

### Post by oldfred on 2012-04-30
I think ext4 is overall the better, only in certain cases were other systems better.

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

### Post by The Cog on 2012-04-30
> Does have linux any filesystem with such excelent ability to survive 
I have been using jfs for years now, and have been very happy with it. I have seen seven instances of ext4 losing huge quantities of data in the 9 months I tried that, so I switched back to jfs again. On rare occasions it needs an fsck after a crash that's unhappy (from a live CD if it's the root partition), but I don't recall ever losing data.

P.S.
I am trying out btrfs this time round, with frequent backups just in case. I like the snapshot capability, and the ability to pool disk space between subvolumes.

---

### Post by masuch on 2012-04-30
Thank you to all for hints.

I have read all benchmarking tests and for main system I am going to stay with ext4 - even for my today created software RAID 0 on revodrive 3 SSD PCI-E hard disk. (still to do make it to boot from raid)

I have also created another 2 software RAIDs 0 - from 3 partitions each on SATA II hard disks for ext4, btrfs , and will create another one for jfs filesystem according to your suggestion (and rsync whole system to it - to see how reliable it is).

The probably last try before I delete btrfs system - going to take from git repository and try btrfsck and btrfs_zero_log to recover it. Interesting you used eatmydata (funny name) for upgrade where I would expected is important sync and ... ?

regards,
M.

---

