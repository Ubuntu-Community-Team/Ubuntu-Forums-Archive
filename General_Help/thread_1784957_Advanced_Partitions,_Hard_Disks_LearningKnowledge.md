---
title: "Advanced Partitions, Hard Disks Learning/Knowledge"
date: 2011-06-17
forum: General Help
---

### Post by johntkucz on 2011-06-17
This thread
[http://ubuntuforums.org/showthread.php?t=267869](http://ubuntuforums.org/showthread.php?t=267869)

looks useful for learning CLI partitioning. Great. 

I will read that, but wnat to learn more.  

Questions I have are:

how does an OS assign external hard disks?  Example: on ubuntu netbook one hard disk is /dev/sdb (1,2,3,4 parttitions)

that's different from the labels I assigned to each partition
/dev/sdb1  1TB300i
/dev/sdb2  2TB200e
/dev/sdb3  3TB300r
/dev/sdb4  4TB100l


that same hard disk plugged into a macos computer (which I dislike btw) shows up as something like /rdisk1 ?

Why is that?  What's going on ? Seems like different operating systems assign different device names to drives?? 

What happens in windows?

Where is the drive locatioN stored?

Where is the drive label stores?

I changed label with
ntfslabel NTFS filesystem
and
e2label ext4 filesystem

but want to understand more of how those get assigned to /dev/sdb1etc

could I assign a drive to say /dev/sdv  ?


Any tutorials, knowledgeable guides, people, or references would be helpful.  Thanks!

---

### Post by bapoumba on 2011-06-17
Moved to General Help.

---

### Post by oldfred on 2011-06-17
I think BIOS assigns drives. On my system it is in motherboard port order. But sometime USB flash drives skip sdd and become sdh or whatever.

Grub when booting sees the boot drive as set by BIOS as hd0. Since I boot sdb it is hd0 and sda then becomes hd1. But once in Ubuntu drives are in same order which ever drive I boot.

Windows also sees drive as drive0, but in windows it is the c: drive. Windows often confuses drives & partitions and you cannot tell them apart in windows. Or d: drive can be just another partition on first drive or another drive with a partition.

You can assign labels to partitions and can use labels to mount drives instead of device (/dev/sda1) or UUID=verylongnumber. You do not have to use labels as a mount point but some systems will default to a label as a mount if a label exists.

I have confused myself by labeling a partition Data or Backup and then mounting it as data or backup. Mount is what is really important.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

