---
title: "partition problems bad superblock"
date: 2011-05-01
forum: General Help
---

### Post by Kaspur on 2011-05-01
I was using my ubuntu 10.10 desktop when I ran into some problems. I downloaded and installed updates and the entire drive went read only. I restarted and could not get back into ubuntu. 

From the live cd I ran fdisk and fsck. I can see the partition and size as /dev/sda2 but fsck returns a zero-length partition:
```

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
37 heads, 29 sectors/track, 456882 cylinders
Units = cylinders of 1073 * 512 = 549376 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c689c68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      229040   122879945+   7  HPFS/NTFS
/dev/sda2          229041      374660    78125130   83  Linux
/dev/sda3          374661      456881    44111566+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fsck -vfy /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 

```

Any help appreciated. I don't really want to wipe the partition yet as there is some data I want to get off it first.

I've attached the screenshot of the gparted partition information too.

---

### Post by srs5694 on 2011-05-01
I'm not familiar with the specific error message, but Googling on ['e2fsck "short read"'](http://www.google.com/search?q=e2fsck+%22short+read%22) turns up several hits. The first two, at least, seem worth reading.

Also, you might want to run a SMART test on the drive, using GSmartControl, smartctl, or something similar. It's conceivable the problem is a symptom of a failing hard disk, in which case you should buy a new one and transfer your data to it *immediately*.

---

