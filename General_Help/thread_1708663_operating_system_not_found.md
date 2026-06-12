---
title: "operating system not found"
date: 2011-03-17
forum: General Help
---

### Post by mohit_hotwani on 2011-03-17
after booting up the computer it says 
operating sytem not found.

result of fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 2030 MB, 2030043136 bytes
63 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00085a14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1015     1982264    c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x115a9de1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
-----------------------------------------------------------------
sda1 is my hard drive that contains ubuntu 10.10(ext4 partition)
and windows vista. Along with these there were 3 more partitions(2 ntfs/fat32(i don't remember) and 1 recovery for vista)
=================================================================
result of boot script:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20202020

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?   761,621,865 2,463,491,804 1,701,869,940  6d Unknown
/dev/sda2     ? 1,701,273,965 3,403,139,995 1,701,866,031  65 Novell Netware 386
/dev/sda3     ?   538,976,288 2,407,685,183 1,868,708,896   a OS/2 Boot Manager
/dev/sda4     ? 1,886,744,434 2,424,286,692   537,542,259  72 Unknown

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda4
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2030 MB, 2030043136 bytes
63 heads, 62 sectors/track, 1015 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00085a14

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,964,589     3,964,528   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x115a9de1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ab7f14b2-252a-40b3-b0ed-862de8458029   ext3                                     
/dev/sdb1        3432-B8F8                              vfat                                     
/dev/sdc1        C646F30546F2F4D1                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/C646F30546F2F4D1  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  3c 3f 78 6d 6c 20 76 65  72 73 69 6f 6e 3d 22 31  |<?xml version="1|
00000010  2e 30 22 20 65 6e 63 6f  64 69 6e 67 3d 22 55 54  |.0" encoding="UT|
00000020  46 2d 38 22 3f 3e 0a 3c  78 62 65 6c 20 76 65 72  |F-8"?>.<xbel ver|
00000030  73 69 6f 6e 3d 22 31 2e  30 22 0a 20 20 20 20 20  |sion="1.0".     |
00000040  20 78 6d 6c 6e 73 3a 62  6f 6f 6b 6d 61 72 6b 3d  | xmlns:bookmark=|
00000050  22 68 74 74 70 3a 2f 2f  77 77 77 2e 66 72 65 65  |"http://www.free|
00000060  64 65 73 6b 74 6f 70 2e  6f 72 67 2f 73 74 61 6e  |desktop.org/stan|
00000070  64 61 72 64 73 2f 64 65  73 6b 74 6f 70 2d 62 6f  |dards/desktop-bo|
00000080  6f 6b 6d 61 72 6b 73 22  0a 20 20 20 20 20 20 78  |okmarks".      x|
00000090  6d 6c 6e 73 3a 6d 69 6d  65 3d 22 68 74 74 70 3a  |mlns:mime="http:|
000000a0  2f 2f 77 77 77 2e 66 72  65 65 64 65 73 6b 74 6f  |//www.freedeskto|
000000b0  70 2e 6f 72 67 2f 73 74  61 6e 64 61 72 64 73 2f  |p.org/standards/|
000000c0  73 68 61 72 65 64 2d 6d  69 6d 65 2d 69 6e 66 6f  |shared-mime-info|
000000d0  22 0a 3e 0a 20 20 3c 62  6f 6f 6b 6d 61 72 6b 20  |".>.  <bookmark |
000000e0  68 72 65 66 3d 22 66 69  6c 65 3a 2f 2f 2f 6d 65  |href="file:///me|
000000f0  64 69 61 2f 30 43 37 36  41 43 35 38 37 36 41 43  |dia/0C76AC5876AC|
00000100  34 34 37 34 2f 66 6f 74  6f 73 2f 6d 61 2f 31 34  |4474/fotos/ma/14|
00000110  31 32 32 30 31 30 34 35  35 2e 6a 70 67 22 20 61  |122010455.jpg" a|
00000120  64 64 65 64 3d 22 32 30  31 30 2d 31 32 2d 32 37  |dded="2010-12-27|
00000130  54 31 32 3a 32 30 3a 30  32 5a 22 20 6d 6f 64 69  |T12:20:02Z" modi|
00000140  66 69 65 64 3d 22 32 30  31 31 2d 30 33 2d 30 35  |fied="2011-03-05|
00000150  54 30 34 3a 30 31 3a 35  33 5a 22 20 76 69 73 69  |T04:01:53Z" visi|
00000160  74 65 64 3d 22 32 30 31  30 2d 31 32 2d 32 37 54  |ted="2010-12-27T|
00000170  31 32 3a 32 30 3a 30 32  5a 22 3e 0a 20 20 20 20  |12:20:02Z">.    |
00000180  3c 69 6e 66 6f 3e 0a 20  20 20 20 20 20 3c 6d 65  |<info>.      <me|
00000190  74 61 64 61 74 61 20 6f  77 6e 65 72 3d 22 68 74  |tadata owner="ht|
000001a0  74 70 3a 2f 2f 66 72 65  65 64 65 73 6b 74 6f 70  |tp://freedesktop|
000001b0  2e 6f 72 67 22 3e 0a 20  20 20 20 20 20 20 20 3c  |.org">.        <|
000001c0  6d 69 6d 65 3a 6d 69 6d  65 2d 74 79 70 65 20 74  |mime:mime-type t|
000001d0  79 70 65 3d 22 69 6d 61  67 65 2f 6a 70 65 67 22  |ype="image/jpeg"|
000001e0  2f 3e 0a 20 20 20 20 20  20 20 20 3c 62 6f 6f 6b  |/>.        <book|
000001f0  6d 61 72 6b 3a 67 72 6f  75 70 73 3e 0a 20 20 20  |mark:groups>.   |
00000200

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
#################################################################
```
hard disk contains very important data that i cant afford to loose.PLease help.

---

### Post by mohit_hotwani on 2011-03-17
please,any help is greatly appreciated.

---

### Post by andrewthomas on 2011-03-17
> **mohit_hotwani said:**
> 
```
**Disk /dev/sda doesn't contain a valid partition table**
Invalid MBR Signature found
/dev/sda1     ?   761,621,865 2,463,491,804 1,701,869,940  6d Unknown
/dev/sda2     ? 1,701,273,965 3,403,139,995 1,701,866,031  65 Novell Netware 386
/dev/sda3     ?   538,976,288 2,407,685,183 1,868,708,896   a OS/2 Boot Manager
/dev/sda4     ? 1,886,744,434 2,424,286,692   537,542,259  72 Unknown

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda4
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda
Unknown MBR on /dev/sda
Unknown BootLoader  on sda1
Unknown BootLoader  on sda2
Unknown BootLoader  on sda3
Unknown BootLoader  on sda4

```**hard disk contains very important data that i cant afford to loose**.PLease help.I hope that you have backed up your data.

What have you tried so far?

---

### Post by mohit_hotwani on 2011-03-17
i am afraid i dont have a backup.

i tried to recover partition table using gpart but it did not work.

---

### Post by Rubi1200 on 2011-03-17
Your best bet for data recovery is probably Testdisk and Photorec:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by mohit_hotwani on 2011-03-19
i tried testdisk too. It listed only one partition correctly.
Is there any other good softwre for prtition table recovery?

---

### Post by mohit_hotwani on 2011-03-23
i was missing something on the testdisk.
It recovered all the partitions.
after reinstalling grub ubuntu was good.
windows is still not booting, winload.exe not found.
I will correct it after some days.
Thanks everyone.

---

