---
title: "Ubuntu not recognizing Windows partition"
date: 2012-07-28
forum: General Help
---

### Post by mblack3nd on 2012-07-28
Hello,

I recently got a new computer and was looking to dual boot. I first cleaned the drive and re-installed Windows 7. Upon loading up the LiveCD both Gparted and the installer fail to recognize the Windows partitions (the C:\ drive and the loader). It just shows a clean, 750 GB drive with unallocated space.

what can I do to fix this.

---

### Post by jerome1232 on 2012-07-28
Shooting for a little more information, what does fdisk show? Open a terminal (ctrl+alt+t) and copy and paste the below code into a terminal, press enter, it will list all of your disks and their partitions.

```
sudo fdisk -l
```

---

### Post by TheFu on 2012-07-28
Could this be a GPT issue?  I suspect more disks will be coming with GPT instead of MBR partition tables going forward.  The version of any disk tool will need to support GPT.  Could the versions of these tools you have be more than a year old?

---

### Post by mblack3nd on 2012-07-28
This is what sudo fdisk -l gave me:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc9336c28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1465143295   732468224    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    40603647    20300800   73  Unknown
/dev/sdb2        40603648    46895103     3145728   84  OS/2 hidden C: drive

Disk /dev/sdc: 4110 MB, 4110417920 bytes
127 heads, 62 sectors/track, 1019 cylinders, total 8028160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdc2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sdc3   ?           0           0           0   6f  Unknown
/dev/sdc4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

```

---

### Post by mblack3nd on 2012-07-28
N.B., my laptop has a "hybrid drive" so there is 24 GB of SSD along with the 750 drive.
---

The LiveCD is a mere few days old...not sure about the tools on them but I assume they are as up to date as can be...

---

### Post by mblack3nd on 2012-08-03
bump

---

### Post by oldfred on 2012-08-03
fdisk is sayinig gpt, but you have MBR partitions. Windows only boots from gpt with UEFI and you do not have an efi partition, so you must have reinstalled in BIOS mode.

If drive was originally gpt and you install Windows in BIOS mode, it erases the primary gpt partition table to convert to MBR, but does not erase the backup. Linux tools see the backup and get confused on whether it is MBR or gpt.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Also the hybrid drives often are configured as RAID. Any drive that was RAID has meta data on the drive and gparted will not then work with that to prevent damage to RAID.

If you are sure you do not want RAID.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

Some Dell's with similar issues.
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

