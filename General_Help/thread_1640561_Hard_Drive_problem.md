---
title: "Hard Drive problem"
date: 2010-12-07
forum: General Help
---

### Post by tonypg on 2010-12-07
Hi i have a Toshiba Qosmiso laptop. Which came with Win 7 (trial).

System specs
intel Core i7 @740@1.73GHz
750gig HD
4gig Ram
1gig nvida Graphics


I have installed Ubuntu and it works great. But for one thing, i have a 750gig HD but form some reason i only have access too 90+gig.

Here is the fdisk -l info...

Code:
Disk /dev/mmcblk0: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         957     1929244+   6  FAT16

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x808876f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       89648   718556160    7  HPFS/NTFS
/dev/sda3           89648       91202    12480512   17  Hidden HPFS/NTFS

More info df -m

Code:
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/loop0               16481     15369       275  99% /
none                      1472         1      1471   1% /dev
none                      1477         2      1475   1% /dev/shm
none                      1477         1      1477   1% /var/run
none                      1477         0      1477   0% /var/lock
/dev/sda2               701715     82158    619558  12% /host
/dev/mmcblk0p1            1884      1789        96  95% /media/3839-6631
Any help would be appreciated.

---

### Post by oldfred on 2010-12-07
I do not know wubi, but you have no Linux partitions, just NTFS windows partitions, so I assume you have a wubi install. That has limits on how large it can be. It is for windows users who want to try Ubuntu for a longer test than just using liveCD, but may want to uninstall easily and not have to worry about creating additional partitions to install Ubuntu into.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

---

