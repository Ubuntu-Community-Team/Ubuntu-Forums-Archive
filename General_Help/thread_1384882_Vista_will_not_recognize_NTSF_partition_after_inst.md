---
title: "Vista will not recognize NTSF partition after install"
date: 2010-01-18
forum: General Help
---

### Post by shadysi on 2010-01-18
First, let me layout my set up.

I have two hard drives, a 320GB and a 1.5TB. The first hard drive has two windows partitions. The first one is the main vista partition and the second one is one for factory restore (its an HP pavilion). 

So wanted to install both ubuntu and ubuntu studio on the second hard drive, so I allocated about 1TB as an ntfs partition that I wanted to be accessible by both vista and ubuntu. So I have 400GB left for both distros. I have partitioned off two 40GB partitions for the two roots and I'm sharing one large home parititon and I put a swap partition at the end of the disk.

After I got through the second installation (ubuntu studio) vista no longer recognised the ntfs partition on the second  disk. I thought maybe the install botched the boot sector, so I used testdisk to try to fix it, but it hasn't done any good. I do not want to format the second drive again because I have data on there I transferred over from an old hard drive before I installed ubuntu.

I tried to 'initialise' the disk in vista, but that just wiped the partition table so I had to fix that with testdisk on a live cd :?

does anyone have any idea how i could possibly fix this problem or what winblows is thinking? I want to be able to read the partition in windows.

```

 sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4246839c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37695   302785056    7  HPFS/NTFS
/dev/sda2           37696       38913     9783585    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa186fb01

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      130234  1046103040    7  HPFS/NTFS
/dev/sdb2          130235      135451    41905552   83  Linux
/dev/sdb3          135452      140668    41905488   83  Linux
/dev/sdb4          140669      182402   335228355    f  W95 Ext'd (LBA)
/dev/sdb5          140669      179968   315677184   83  Linux
/dev/sdb6          179970      182401    19535032   82  Linux swap / Solaris


```

---

### Post by shadysi on 2010-01-19
bump, anyone have any ideas?

---

### Post by shadysi on 2010-01-21
Well... since no one helped me, I figured it out..

My grub boot disk had partition was GPT, while the main system was MBR partitioned. This does NOT work out of the box apparently. After pounding my head against the wall and reformatting the second hard drive several times, I completely wiped it and tried with a MBR type partitioning instead and I had no issues after that.

I also found the bug in the grub2 tracking system if anybody wants a more precise description of the problem.

"BIOS-type computer with GPT bootdisk doesn't find filesystem(s) on another disk which is MBR/msdos type"

[http://savannah.gnu.org/bugs/?27920](http://savannah.gnu.org/bugs/?27920)

---

