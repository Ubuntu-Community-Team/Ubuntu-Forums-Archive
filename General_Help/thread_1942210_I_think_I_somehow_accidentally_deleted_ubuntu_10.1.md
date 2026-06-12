---
title: "I think I somehow accidentally deleted ubuntu 10.11"
date: 2012-03-17
forum: General Help
---

### Post by tasha8694 on 2012-03-17
So I somehow think I accidentally deleted ubuntu 10.11 on my laptop. When I try and boot it, it automatically goes into grub rescue and says the partition (originally hd0,msdos6) cannot be found. Booting ubuntu from the live cd lets me find a couple things out:

first "fdisk -l" displays this:
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x94f2f74f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    36866047    18432000   27  Hidden NTFS WinRE
/dev/sda2   *    36866048    37070847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        37070848  1054364010   508646581+   7  HPFS/NTFS/exFAT
/dev/sda4      1054365694  1250263039    97948673    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1238007808  1250263039     6127616   82  Linux swap / Solaris

and "df -Th" gives me:
Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    2.9G   41M  2.9G   2% /
udev      devtmpfs    2.9G  4.0K  2.9G   1% /dev
tmpfs        tmpfs    1.2G  828K  1.2G   1% /run
/dev/sr0   iso9660    698M  698M     0 100% /cdrom
/dev/loop0
          squashfs    663M  663M     0 100% /rofs
tmpfs        tmpfs    2.9G  8.0K  2.9G   1% /tmp
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    2.9G  104K  2.9G   1% /run/shm

Lastly gparted shows that there is a section of 87.57 GiB of unallocated space. I originally had ubuntu installed with about this much space. 

So my real question is if I can get ubuntu back without losing all my data? Or is my only option to reinstall it?

Also it originally was set up as a duel boot with Windows 7, I also don't want to lose any of the data in there, would a re-install do any damage to it?

---

### Post by jerrrys on 2012-03-17
You can try testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Helen McCall on 2012-03-17
After you installed Ubuntu, did you use any partition editor again?

The /dev/sda4 partition is the extension in which you have created at least two extended partitions. Only one of these remains: the Linux swap partition at the end of it. The Linux partition before that has been deleted. You need to use parted or gparted to recreate a new partition of ext4 or ext3 whichever you prefer, and then you will need to re-install on that partition.

---

### Post by tasha8694 on 2012-03-18
> **Helen McCall said:**
> After you installed Ubuntu, did you use any partition editor again?

The /dev/sda4 partition is the extension in which you have created at least two extended partitions. Only one of these remains: the Linux swap partition at the end of it. The Linux partition before that has been deleted. You need to use parted or gparted to recreate a new partition of ext4 or ext3 whichever you prefer, and then you will need to re-install on that partition.

No I did not use the partition editor again after I installed it.

Okay so if I recreate a partition of it (which I'm not sure how to do) and reinstall it will I loose all my previous files on my laptop?

---

