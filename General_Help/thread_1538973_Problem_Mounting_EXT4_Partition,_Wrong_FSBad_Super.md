---
title: "Problem Mounting EXT4 Partition, Wrong FS/Bad Superblock/Bad Option"
date: 2010-07-25
forum: General Help
---

### Post by colecampbell666 on 2010-07-25
I'm trying to mount an EXT4 partition from my laptop, and it won't mount.

My laptop died, so I put my boot drive into a USB enclosure, and plugged it into another PC. There are 4 partitions on the drive, Linux Swap (Dunno), Ubuntu 10.04-64 (EXT4), Windows 7 (NTFS) and a FAT32 partition. The NTFS and FAT32 partitions read fine using an Ubuntu Live CD or Windows, however the main Ubuntu partition won't read under either. 

I tried using various EXT2 drivers/readers under Windows (none are available for EXT4), and none worked, and when I try to mount the partition using the Live CD (10.04-32), it gives me the following error:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I'm assuming it's calling the wrong FS driver up, and I can't think of why, and don't know how to change it (which I'll probably Google in the morning). What concern(s?) me are the other two errors, about bad blocks and such. 

Any input? I don't assume it's a 64-bit vs. 32-bit discrepancy, seeing as that variable is independent of the filesystem, but I'm at a loss as to what could be wrong. I don't think it's due to the enclosure, seeing as the other partitions mount fine, and that rules out drive failure as well (Or does it? Can drive failure be "localized"?)

---

### Post by colecampbell666 on 2010-07-26
Bump.

---

