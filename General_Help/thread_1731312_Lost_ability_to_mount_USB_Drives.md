---
title: "Lost ability to mount USB Drives"
date: 2011-04-17
forum: General Help
---

### Post by kenbo on 2011-04-17
I've been using 10.10 for almost a year with no problems. Then last week I plugged in my MP3 player (ONDA vx777le) and it did not automount as it usually does. I have since found that any USB stick will not mount any more either.

They show up in lsusb
```
ken@ken-desktop:~$ lsusb
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 071b:3203 Domain Technologies, Inc. Rockchip Media Player
Bus 001 Device 004: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8192SU]
Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But not in fdisk -l
```
ken@ken-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3c78429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25180   202258318+   7  HPFS/NTFS
/dev/sdb2           25181       30401    41937682+   5  Extended
/dev/sdb5           25181       30401    41937651    b  W95 FAT32

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d26b218

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23100   185546875    7  HPFS/NTFS
/dev/sda2           28471       38914    83884032    7  HPFS/NTFS
/dev/sda3           23100       28471    43138049    5  Extended
/dev/sda5           23100       28471    43138048   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xafb3afb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       95952   770734408+   7  HPFS/NTFS
/dev/sdc2           95953      121602   206026753    5  Extended
/dev/sdc5           95953       96451     3999744   82  Linux swap / Solaris
/dev/sdc6           96451      121602   202025984   83  Linux

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa729a729

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2        7885    63328230    f  W95 Ext'd (LBA)
/dev/sdd2   *        7886       24792   135805477+   c  W95 FAT32 (LBA)
/dev/sdd5               2        7885    63328198+   7  HPFS/NTFS

```

I also see this in messages when I plug it in:
```
Apr 17 01:40:21 ken-desktop kernel: [24379.152035] usb 1-4: new high speed USB device using ehci_hcd and address 14

```


I'm assuming This happened with some update but I don't know what one. 

Any ideas?

---

### Post by kenbo on 2011-04-17
I don't know why. (as I was not getting the error's he was getting) but this thread worked.

[http://ubuntuforums.org/showthread.php?p=9376116]("http://ubuntuforums.org/showthread.php?p=9376116")

---

