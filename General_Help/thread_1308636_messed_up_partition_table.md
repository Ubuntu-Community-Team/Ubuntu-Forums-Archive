---
title: "messed up partition table"
date: 2009-10-31
forum: General Help
---

### Post by haron.sarwar on 2009-10-31
Hi Guys,

Please help, I use Ubuntu 8.10 and lately have not been able to boot into it after using swissknif ( a FAT32 partitioner) on an external drive in windows.
My installation is in the sencond partition of the second drive and grub is installed on the partition itself not in MBR i.e. I use Vista boot manager not Grub for the three OS.
I know the problem is not my boot loader but the partition table, it has been alterd somehow when I used the mentioned software.
Here is the info from fdisk -l /dev/sdb command.



[B][I]ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ab54ab4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15541   124832058+   7  HPFS/NTFS
/dev/sdb2           15541       19457    31456608+  83  Linux
ubuntu@ubuntu:~$ gksu gparted /dev/sdb
======================
libparted : 1.8.9
======================
Can't have overlapping partitions.
ubuntu@ubuntu:~$

I don't know how to fix this, please could someone come up with a solution as I have put a lot of time into tailoring it to the way I wanted it and don't want to loose it all, not to mention my data. And Yes I had a recent backup of it in an external hard drive but last week when I got home from work my three year old who somehow got hold of it from a very hard to reach place was playing with it and you can guess the rest.

Go easy I am not very experienced with Linux.

Thanks in advance,

---

