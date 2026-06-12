---
title: "Usb Hard Drive Problem"
date: 2011-03-16
forum: General Help
---

### Post by CrusaderAD on 2011-03-16
Hey guys, I got a bit of a problem with a usb hard drive. A friend brought it up to me and he has nearly a terabyte of data he needs. The hard drive case broke, so he bought a new one. No problem. We got it powered back on and it seems like I can see it (at least in gparted I can). Gparted reports that it is all unallocated space. I was reading around and it might be because it wasn't safely removed and that might have messed something up. Also, he used it with a mac... so it's a hfs file system. Any ideas? Help!

---

### Post by CrusaderAD on 2011-03-29
Bump

---

### Post by PoHandle on 2011-03-29
If GParted is showing only unallocated space, and you are absolutely sure that there is data within a formatted partition on the drive, you may want to try to recover the partition table.  The method described at [https://help.ubuntu.com/community/DataRecovery#GNU Parted](https://help.ubuntu.com/community/DataRecovery#GNU Parted) has worked for me in the past.

I'm not sure if it's still an issue, but I recall having to go through a process to disable journaling to work with HFS partitions.  I have little experience with using HFS partitions.

---

### Post by CrusaderAD on 2011-03-29
Hey thanks for the suggestion and link! I'm trying testdisk now with the analyze apple option. Should be done in about 5-6 hours. Fingers crossed!

---

### Post by CrusaderAD on 2011-03-31
I ran testdisk and it logged everything and said to run pdisk. Apparently I can run fdisk on ubuntu and it will restore the partition table. The problem is I don't know what the start and end is on the table. This is the log:

> Tue Mar 29 12:02:56 2011
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.32-30-generic (#59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488281250 sectors
/dev/sda: user_max   488281250 sectors
/dev/sda: native_max 488281250 sectors
/dev/sda: dco        488397168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30394 255 63, sector size=512 - ATA SAMSUNG HD251HJ
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - Generic External

Partition table type (auto): Intel
Disk /dev/sdd - 1000 GB / 931 GiB - Generic External
Partition table type: Mac

Analyse Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
Bad MAC partition, invalid block0 signature
read_part_mac: bad DPME signature

search_part()
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63
check_FAT: Bad jump in FAT partition

HFS+ magic value at 121553/57/9
part_size 313992
     HFS                   1952752544 1953066535     313992
     HFS+, 160 MB / 153 MiB

Results
   P HFS                   1952752544 1953066535     313992
     HFS+, 160 MB / 153 MiB

interface_write()
   P HFS                   1952752544 1953066535     313992
Function write_part_mac not implemented

TestDisk exited normally.

Any ideas?

---

### Post by CrusaderAD on 2011-04-01
Anyone out there that can help me read this log? I'm unable to find any examples that list what each value is.

---

### Post by PoHandle on 2011-04-01
Unfortunately, I do not know how to proceed in this case.  Back when I had to recover a partition, it was a FAT32 partition, and I don't have much experience with HFS.  I found something that might help you out though:

[http://abhinay.wordpress.com/2009/04/12/repair-fix-mac-hfs-partition-using-ubuntu-cd/](http://abhinay.wordpress.com/2009/04/12/repair-fix-mac-hfs-partition-using-ubuntu-cd/)

---

