---
title: "Iomega HDD: not detected in gparted!"
date: 2012-05-14
forum: General Help
---

### Post by astrobob.tk on 2012-05-14
I just got an Iomega Prestige 1TB portable HDD & plugged it in. I got two nautilus windows: Iomega_HDD & Virtual CD. The latter contains Iomega encryption utility for Mac & Windows.

I opened gparted to format it to ext4 but it is not detected, so I right clicked on the desktop icon & formatted it to ext4, but still it is not detected in gparted!

Here's some cli results:

```
$dmesg
.
.
.
[ 9623.452058] usb 2-1: new high speed USB device using ehci_hcd and address 9
[ 9626.865066] usb 2-1: configuration #1 chosen from 1 choice
[ 9626.873652] scsi13 : SCSI emulation for USB Mass Storage devices
[ 9626.873992] usb-storage: device found at 9
[ 9626.873997] usb-storage: waiting for device to settle before scanning
[ 9631.873127] usb-storage: device scan complete
[ 9631.883591] scsi 13:0:0:0: Direct-Access     OEM      Ext Hard Disk    0000 PQ: 0 ANSI: 5
[ 9631.902688] scsi 13:0:0:1: CD-ROM            Virtual  CDROM                 PQ: 0 ANSI: 0
[ 9631.903927] sd 13:0:0:0: Attached scsi generic sg2 type 0
[ 9631.980280] sd 13:0:0:0: [sdb] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[ 9632.011386] sr1: scsi-1 drive
[ 9632.011692] sr 13:0:0:1: Attached scsi CD-ROM sr1
[ 9632.011858] sr 13:0:0:1: Attached scsi generic sg3 type 5
[ 9632.033827] sd 13:0:0:0: [sdb] Write Protect is off
[ 9632.033837] sd 13:0:0:0: [sdb] Mode Sense: 10 00 00 00
[ 9632.033844] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 9632.106517] sd 13:0:0:0: [sdb] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[ 9632.148148] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 9632.148163]  sdb: sdb1
[ 9632.298383] sd 13:0:0:0: [sdb] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[ 9632.339641] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 9632.339651] sd 13:0:0:0: [sdb] Attached SCSI disk
[ 9633.653326] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 9633.678577] ISOFS: changing to secondary root
[ 9634.133808] EXT4-fs (sdb1): mounted filesystem with ordered data mode

``````
$ dmesg|grep sdb
[16316.166031] sd 15:0:0:0: [sdb] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[16316.219651] sd 15:0:0:0: [sdb] Write Protect is off
[16316.219661] sd 15:0:0:0: [sdb] Mode Sense: 10 00 00 00
[16316.219667] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[16316.291590] sd 15:0:0:0: [sdb] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[16316.333657] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[16316.333672]  sdb: sdb1
[16316.481291] sd 15:0:0:0: [sdb] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[16316.522536] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[16316.522546] sd 15:0:0:0: [sdb] Attached SCSI disk
[16318.237260] EXT4-fs (sdb1): mounted filesystem with ordered data mode
``````
$fdisk -l
.
.
.
Disk /dev/sdb: 999.5 GB, 999470882816 bytes
255 heads, 63 sectors/track, 15189 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5dceb3fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15188   975980628    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.

``````
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 059b:0070 Iomega Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
$ df -ah
Filesystem            Size  Used Avail Use% Mounted on
.
.
.

/dev/sr1               21M   21M     0 100% /media/Virtual CD
/dev/sdb1             917G  200M  870G   1% /media/Iomega
```My questions are:

1) Why is it not detected by gparted?
2) Do I have to be concerned about that?
3) Can I delete this "Virtual Cd"? And add it to the main partition?
4) Would it be better to partition the HDD to several partitions?

Thanks in advance

===**Update**===

I just thought of launching gparted from terminal & apparently:

```
$gparted
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon
astrobob@astrobob-laptop:~$ sudo gparted
======================
libparted : 2.2
======================
Device /dev/sdb has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Ignoring device /dev/sdb with logical sector size of 4096 bytes because gparted only supports a size of 512 bytes.
```

---

### Post by astrobob.tk on 2012-05-17
bump!

---

### Post by astrobob.tk on 2012-06-25
Since my last post I had live support from Iomega & the guy was great. He asked me logical questions & obviously my fears have gone.

I formatted it to ext4 & copied about 450GB of data from my HDD to the new Iomega. I do not use it on a daily basis, its just for archiving; when i need something I grab it from it.

For now it has been working without any problem.

I guess any HDD should work with Linux. There's no reason why it shouldn't.

---

