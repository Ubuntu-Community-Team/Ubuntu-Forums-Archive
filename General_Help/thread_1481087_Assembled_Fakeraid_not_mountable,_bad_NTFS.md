---
title: "Assembled Fakeraid not mountable, bad NTFS"
date: 2010-05-12
forum: General Help
---

### Post by GMU_ninja on 2010-05-12
Hello,

I am attempting to reassemble and mount a fake raid array that I created for Windows.  The array is a RAID 5 array with one NTFS partition.  The array works properly and is accessible in Windows.

I say fake raid because the BIOS presents it to Windows as one drive (using drivers, I suppose).  Motherboard is a [BIOSTAR TA790GXE 128M]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138146").

The root partition and swap are on an ATA drive (sde5 and sde6) along with the Windows OS (sde2).  This RAID array (4 SATA drives) was created for backup storage and large amounts of data.

This is what I tried:
```
$ sudo mdadm --assemble /dev/md0 /dev/sd{a,b,c,d}
mdadm: /dev/md0 has been started with 4 drives.

$ sudo mount -t ntfs /dev/md0 /mnt/Storage
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

Here are the partition tables according to fdisk:
```
Disk /dev/md0: 960.2 GB, 960218529792 bytes
2 heads, 4 sectors/track, 234428352 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0xee130c7d

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1e733fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      116714   937497600    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee130c7d

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ff43f87

Disk /dev/sdd doesn't contain a valid partition table

```
I should note that while the partition table shows a /dev/sda1 partition, the block device doesn't exist.  If I try to mount it, this is the error I get:
```
$ sudo mount -t ntfs /dev/sda1 /mnt/Storage
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory
```

Thanks for reading!  Any help would be appreciated!

Output of mdadm --detail /dev/md0:
```
/dev/md0:
        Version : 00.90
  Creation Time : Sun Feb 15 21:59:34 2009
     Raid Level : raid5
     Array Size : 937713408 (894.27 GiB 960.22 GB)
  Used Dev Size : 312571136 (298.09 GiB 320.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May 12 08:17:51 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 97b0e671:4763bb6b:01f9e43d:ac30fbff
         Events : 0.1166

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8        0        1      active sync   /dev/sda
       2       8       48        2      active sync   /dev/sdd
       3       8       32        3      active sync   /dev/sdc
```

---

### Post by john newbuntu on 2010-05-12
Correct me if I am wrong.  You mentioned that your system supports fakeraid and I am assuming you have it enabled in BIOS.  Are you also trying to set up a software raid on the fake raid devices?  I think this will corrupt your data.  As I understand it, you need to use "dmraid" command to set up fakeraid in Ubuntu.  The raid array setup will be done at the BIOS level.  This way, you can create/grow/sync devices of the array at the BIOS level rather than at the OS level.  You will be accessing devices under /dev/mapper/ to install linux.  A little more information is available at:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If I have got this wrongly and if these devices are not part of the fake raid array, then you can use mdadm with the appropriate options to create software raid array.  But you would
have to partition and format the devices first before using them.

---

### Post by GMU_ninja on 2010-05-13
Thanks for the reply!

You are correct that I am using the BIOS Fake RAID feature.  I am trying to assemble a RAID array I already created in the BIOS option.

Unfortunately, I have already read through the FakeRaidHowto page and it doesn't really help me (perhaps I am not understanding).  Since I already have Ubuntu installed on another disk, I don't know how to get dmraid to detect and assemble the array.

Ubuntu is recognizing the disks as /dev/sda through sdd.  There is nothing useful showing up in /dev/mapper/ either.

After a fresh reboot (array is still functional in Windows and BIOS):
```
$ dmraid -V
dmraid version:		1.0.0.rc16 (2009.09.16) shared 
dmraid library version:	1.0.0.rc16 (2009.09.16)
device-mapper version:	unknown
$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root 10, 59 2010-05-13 09:00 control

```

I tried messing around with the dmraid tool:
```

$ sudo dmraid -r
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
/dev/sde: via, "via_echjbhicef", unknown, ok, 625142447 sectors, data@ 0
/dev/sdd: via, "via_echjbhicef", unknown, ok, 625142447 sectors, data@ 0
/dev/sdc: via, "via_echjbhicef", unknown, ok, 625142447 sectors, data@ 0
/dev/sdb: via, "via_echjbhicef", unknown, ok, 625142447 sectors, data@ 0

$ sudo dmraid -ay
ERROR: pdc: zero sectors on /dev/sde
ERROR: pdc: setting up RAID device /dev/sde
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
ERROR: via: RAID type 5 not supported
ERROR: adding /dev/sde to RAID set "via_echjbhicef"
ERROR: via: RAID type 5 not supported
ERROR: adding /dev/sdd to RAID set "via_echjbhicef"
ERROR: via: RAID type 5 not supported
ERROR: adding /dev/sdc to RAID set "via_echjbhicef"
ERROR: via: RAID type 5 not supported
ERROR: adding /dev/sdb to RAID set "via_echjbhicef"
ERROR: no RAID set found
no raid sets

$ dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs


```

I guess the problem is the RAID set or metadata format is not supported?  Is there any way I can add support?

Thanks for reading!

---

### Post by john newbuntu on 2010-05-13
To be honest, I have never assembled a fake raid and I hope somebody can chip in here to help.  But looking at the output you have posted, it appears that the raid array setup is not complete as shown by dmraid -ay.  You are also getting errors with the metadata format handler.

The way I understand fakeraid, you need to set it up in BIOS.  From then on, when you install Ubuntu, it should be from a liveCD/USB into /dev/mapper device as indicated by gparted.  You should not be partitioning or formatting any of your array devices.

I searched the forum and found a post on how someone got it to work on Gutsy:
[http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)
The information needs update but you get the idea on how the thing works.

At this point, I am not sure on how the array would function since you have installed Ubuntu on to an array device.  If feel that you might have to uninstall Ubuntu, remove the raid devices, disable raid in the BIOS, redo the array and install ubuntu on /dev/mapper.  I would however wait to hear from someone who is familiar with fakeraid and who has done these before.

---

### Post by GMU_ninja on 2010-05-13
Thanks for the reply again!

Yea... at this point I don't think there is any hope of me reassembling the fake RAID array in Ubuntu.  If anyone else knows better, please let me know!

Ubuntu and Windows are NOT installed on the array.  It is installed on a separate ATA drive (sde).  The array consists of four SATA drives (sda, sdb, sdc, sdd).  The array works in Windows (setup as drive D: for large storage and backups).  I am trying to make it shared storage for both OS's.

Anyone with more info, please let me know.  Thanks!

---

