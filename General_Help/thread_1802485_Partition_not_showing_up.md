---
title: "Partition not showing up"
date: 2011-07-12
forum: General Help
---

### Post by saruji on 2011-07-12
Objective: To dual boot Ubuntu 11.04 and Windows 7

Problem: When I use Live USB and try to install Ubuntu 11.04, two of my partitions are not showing up.

System:
C2D 3.1 Ghz
6 Gb of Ram
Nvidia 8800 gt

More info:
I have a self built machine which is currently running windows 7 64 bit.

4 hard drives
2 x 1 TB (mirrored)
1 x 500 Gb (single)
1 x 320* Gb (Windows 7 is installed here) <--both do not show up in the installer
*Split into 247 Gb and 73.4 Gb partitions

[[IMG]http://i.imgur.com/bNOZb.png[/IMG]](http://imgur.com/bNOZb)

fdisk -l output
```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76a81caa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29989   240880608+   7  HPFS/NTFS
/dev/sda2           29989       38914    71690240   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb481

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3f268a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 8011 MB, 8011120640 bytes
246 heads, 40 sectors/track, 1590 cylinders
Units = cylinders of 9840 * 512 = 5038080 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2        1591     7815296    c  W95 FAT32 (LBA)

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3f268a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/dm-0: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3f268a3

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/dm-1: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

Parted output
```

Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  247GB  247GB   primary  ntfs         boot
 2      247GB   320GB  73.4GB  primary  ext4


Model: ATA SAMSUNG HE502IJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs


Model: ATA SAMSUNG HE103UJ (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model:  Patriot Memory (scsi)
Disk /dev/sdd: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      8258kB  8011MB  8003MB  primary  fat32        boot, lba


Model: ATA SAMSUNG HE103UJ (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/nvidia_adcdacjb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs
```

*This happens in Ubuntu 10.10 and 11.04, the screen shot above was taken in 10.10.
Also I can mount the 247 Gb partition in the Live USB, however doing so does not make it show up in the installer.

Things I have tried:
Unplugging all of the hard drives except for the 320 Gb hard drive, as a result not drives showed up in the installer but where present in Gparted and "Places"

Thank you,
-S

---

### Post by saruji on 2011-07-13
bump? Any ideas on where to go and look?

---

### Post by oldfred on 2011-07-13
I know nothing about RAID but these may help:

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Mark Phelps on 2011-07-13
I'm somewhat confused by your comments ...

You say the 500GB and the mirrored 1TB drives are "not showing up in the installer" -- but the screen shot shows them.

As to drives being selectable in the installer, only the 73GB Ext partition should be available; the others are NTFS and should NOT show as available.

Am I missing something here?

---

### Post by saruji on 2011-08-15
> **Mark Phelps said:**
> I'm somewhat confused by your comments ...

You say the 500GB and the mirrored 1TB drives are "not showing up in the installer" -- but the screen shot shows them.

As to drives being selectable in the installer, only the 73GB Ext partition should be available; the others are NTFS and should NOT show as available.

Am I missing something here?

I am sorry, what I meant to say was that.  I have a 500 GB HD a raid 1 with a 2x1 tb drives I also have a 320 GB hard drive, what I would like is to install to the 320 GB drive.  The 320 Gb drive has Win 7 installed.  However I "shrunk" the 320 Gb drive with Win 7 on it, by 73GB, which I would like to use to install Ubuntu.  Any further thoughts would be appreciated.

Thank you,

---

### Post by oldfred on 2011-08-18
Then it should be a standard install to your 320GB install. Do you have all 4 primary partitions used? If not you can create the extended partition and install to that.

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-11.04-natty-narwhal-with-ubuntu-classic](http://www.howtoforge.com/the-perfect-desktop-ubuntu-11.04-natty-narwhal-with-ubuntu-classic)

---

