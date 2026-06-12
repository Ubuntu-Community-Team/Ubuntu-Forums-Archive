---
title: "Windows fails to access NTFS partition after installing ubuntu"
date: 2009-12-27
forum: General Help
---

### Post by mrpaint on 2009-12-27
Hi,

I'm new to *nix world. I have just install Uubuntu (9.10) dual-boot with my XP a few days ago. I spent several days playing around in Ubuntu and figured out plenty of things but today, when I get back to XP, it's extremely slow and the most important thing is XP can't access to one of my partition. Here is the detail of my partitions (`sudo fdisk -l` in Ubuntu)

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1963    15727635    7  HPFS/NTFS
/dev/sda3           16847       19457    20972857+  83  Linux
/dev/sda4            1964       16846   119547697+   f  W95 Ext'd (LBA)
/dev/sda5            1964        7185    41945683+   7  HPFS/NTFS
/dev/sda6            7186       16846    77601951    b  W95 FAT32


I have mounted (both manually and permanently) /dev/sda5 and /dev/sda6. As you can see in the result, Ubuntu is installed in /dev/sda3. XP is installed in /dev/sda2. Ubuntu works great, access to partitions normally but XP fails to access /dev/sda5 (which is a NTFS partition)

Please note that, XP ran in to BSOD 2 times (IRQL is not less or equal), after that XP ran chkdsk against /dev/sda5 and /dev/sda6. Here is the result of /dev/sda5 chkdsk session (grab from file /dev/sda5/bootex.log in Ubuntu)

```
Checking file system on D:
The type of the file system is NTFS.
Volume label is APPS.


One of your disks needs to be checked for consistency. You
may cancel the disk check, but it is strongly recommended
that you continue.
Windows will now check the disk.                         
The file reference 0x1000000000019 of index entry $ObjId of index $I30
with parent 0xb is not the same as 0x2000000000019.
Deleting index entry $ObjId in index $I30 of file 11.
Unable to locate the file name attribute of index entry $Quota
of index $I30 with parent 0xb in file 0x18.
Deleting index entry $Quota in index $I30 of file 11.
The index attribute of type 0x0 for index root $O
in file 0x18 is not indexable.
Removing corrupt index $O in file 24.
The index attribute of type 0x0 for index root $Q
in file 0x18 is not indexable.
Removing corrupt index $Q in file 24.
Cleaning up minor inconsistencies on the drive.
Creating object id file.
Inserting an index entry into index $I30 of file 11.
Creating index $O for file 17.
The object id in file 0x3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x26 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x37 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x100 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x479 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x48c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4f3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x57b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x580 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x583 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x584 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x586 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x590 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5a9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5f2 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5f3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x66b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6b5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x7cd does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x910 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x916 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x922 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x92a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x92f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x998 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x99a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xeea does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xf16 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xf38 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xf96 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xfb3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xfb4 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12af does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12c6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12e6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x157b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1582 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1661 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1663 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1668 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x166a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x16a9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x16ae does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x16af does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x16b0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x16d9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x171e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x21b0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x2244 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x2269 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x252b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x267d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x286a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x31d6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x338e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x33bd does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x33cc does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x38c7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x38d0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x38d2 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x38d9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x3ba4 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x3ba5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x3bad does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x3edb does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x3fd5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x40c3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x44c3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x44c8 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4513 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x451f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4525 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4af8 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4e8f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4f08 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4f2a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4f53 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4f57 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4fa0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4fa1 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4fa6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x4fa7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x513a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5152 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x51f6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x530e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5313 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5368 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x540a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x540e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x540f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x561d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x562c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x57a9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x57fd does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5859 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5887 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5888 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x58bd does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x58f6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x58f7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5e67 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x5eb2 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6241 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6250 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6251 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x62e3 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x632f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x634d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x639d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x639e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x65de does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6aeb does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6b08 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6b2c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6bd0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6c28 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x6c2c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0xfff8 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10045 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1004f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10075 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x100aa does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x100b8 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1021b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10238 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1098f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x109b5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10d02 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10dc6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10df5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10df6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x10df8 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1139c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1140e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1140f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11646 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1164a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x116ff does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x117c2 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x117c7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1180b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1183c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x118d7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11c5b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11c8c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11cdf does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11d0e does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11f33 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11fea does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11feb does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x11fee does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x120d2 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x120d4 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x120d9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12146 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12147 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1294f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12a8d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12a92 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12cda does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x12cdb does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x14ca4 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x15ffb does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x16498 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x164a6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x164c1 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1652c does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1655a does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1680d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1680f does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x17470 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x174aa does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177b7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177be does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177c0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177d6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177e7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177e9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x177f0 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x17801 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x17d08 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x17e32 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x18a50 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x18a8b does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x18c92 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x18cd7 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x18eb9 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x1959d does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195a1 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195a2 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195a5 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195ad does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195af does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195b6 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
The object id in file 0x195b8 does not appear in the object
id index in file 0x11.
Inserting an index entry into index $O of file 17.
Creating quota file.
Inserting an index entry into index $I30 of file 11.
Creating index $O for file 18.
Creating index $Q for file 18.
Inserting default quota record into index $Q in file 18.
Cleaning up 101 unused index entries from index $SII of file 0x9.
Cleaning up 101 unused index entries from index $SDH of file 0x9.
Cleaning up 101 unused security descriptors.
CHKDSK is verifying Usn Journal...
Usn Journal verification completed.
Correcting errors in the master file table's (MFT) BITMAP attribute.
Correcting errors in the Volume Bitmap.
Windows has made corrections to the file system.

  41945680 KB total disk space.
  28130324 KB in 96273 files.
     40188 KB in 7567 indexes.
         0 KB in bad sectors.
    210280 KB in use by the system.
     65536 KB occupied by the log file.
  13564888 KB available on disk.

      4096 bytes in each allocation unit.
  10486420 total allocation units on disk.
   3391222 allocation units available on disk.

Internal Info:
a0 a8 01 00 aa 95 01 00 bf cf 02 00 00 00 00 00  ................
c6 00 00 00 00 00 00 00 c4 00 00 00 00 00 00 00  ................
0a f4 ae 07 00 00 00 00 48 78 db 40 00 00 00 00  ........Hx.@....
f2 13 51 08 00 00 00 00 00 00 00 00 00 00 00 00  ..Q.............
00 00 00 00 00 00 00 00 f6 cf 73 5c 00 00 00 00  ..........s\....
99 9e 36 00 00 00 00 00 a0 3a 07 00 11 78 01 00  ..6......:...x..
00 00 00 00 00 50 f0 b4 06 00 00 00 8f 1d 00 00  .....P..........

```

Chkdsk found no errors in /dev/sda6
After the chkdsk, still unable to acess /dev/sda5 in XP. But when I get back to Ubuntu (now), accessing to /dev/sda5 has no problem at all!

Please help!

---

### Post by pastalavista on 2009-12-27
Did you defrag your Windows before you installed Ubuntu? It might possibly help if you did that now, but if you had file fraagments caught out when you resized the partition, they could be gone now. This could be the case, especiaally if you had .exe .bin .dll files etc stored on that drive.

[ps.. next time you have so much text to paste, use the ```
code goes here
``` tags so it won't hog the whole page]

---

### Post by mrpaint on 2009-12-27
> **pastalavista said:**
> Did you defrag your Windows before you installed Ubuntu? It might possibly help if you did that now, but if you had file fraagments caught out when you resized the partition, they could be gone now. This could be the case, especiaally if you had .exe .bin .dll files etc stored on that drive.

[ps.. next time you have so much text to paste, use the ```
code goes here
``` tags so it won't hog the whole page]
Thanks for your quick reply

The Ubuntu partition is the one I use all the time to install second OS (including other version of Windows or Linux) so I didn't resize partitions to install Ubuntu this time. Any guesses?

PS: I tried, I used the QUOTE tag. Which tag should I use instead? Please advise. Thank you again

**Edit: Oops, now I see your CODE tag. Edited the first post**

---

### Post by pastalavista on 2009-12-27
> **mrpaint said:**
> Thanks for your quick reply

The Ubuntu partition is the one I use all the time to install second OS (including other version of Windows or Linux) so I didn't resize partitions to install Ubuntu this time. Any guesses?

PS: I tried, I used the QUOTE tag. Which tag should I use instead? Please advise. Thank you again

**Edit: Oops, now I see your CODE tag. Edited the first post**

I should have said CODE tags instead of 'code goes here'.. my bad. I notice you also have FAT32 on the same extended partition. My guess is malware spread around the Widows partitions. You could try booting from Windows install disk and repairing the drive. Of course, then you'd most likely need to reinstall grub which is no biggie. Or you could try booting from a [Rescue CD]("http://www.sysresccd.org/Download") or [Supergrub Disk]("http://www.supergrubdisk.org/") but the Windows disk will probably fix it.

---

### Post by theozzlives on 2009-12-27
I'd say post a screenshot of your gparted screen, see what it has to say.

---

### Post by mrpaint on 2009-12-27
> **pastalavista said:**
> I should have said CODE tags instead of 'code goes here'.. my bad. I notice you also have FAT32 on the same extended partition. My guess is malware spread around the Widows partitions. You could try booting from Windows install disk and repairing the drive. Of course, then you'd most likely need to reinstall grub which is no biggie. Or you could try booting from a [Rescue CD]("http://www.sysresccd.org/Download") or [Supergrub Disk]("http://www.supergrubdisk.org/") but the Windows disk will probably fix it.

I ran bootsec.exe from the Windows Install CD to fix the MBR before (need to remove Windows 7 loader to use the legacy Windows XP loader)

> **theozzlives said:**
> I'd say post a screenshot of your gparted screen, see what it has to say.
Screenshot attached. Please advise. Thank a lot

---

### Post by SecretCode on 2009-12-27
So you didn't move the sda5 partition during this installation? And sda3, the ext4 primary partition at the end, has always been there?

Hmm ... can you install **disktype** and run
```
sudo disktype /dev/sda
```
[SIZE="1"]Post the output in code tags[/SIZE] :)

---

### Post by mrpaint on 2009-12-27
> **SecretCode said:**
> So you didn't move the sda5 partition during this installation? And sda3, the ext4 primary partition at the end, has always been there?

Hmm ... can you install **disktype** and run
```
sudo disktype /dev/sda
```
[SIZE="1"]Post the output in code tags[/SIZE] :)
Yeah, they are there before. Worked well with several combinations of OSes before. And here goes the result. Hope it helps

```
--- /dev/sda
Block device, size 149.1 GiB (160041885696 bytes)
DOS/MBR partition map
Partition 1: 39.19 MiB (41094144 bytes, 80262 sectors from 63)
  Type 0xDE (Dell Utility)
  Windows NTLDR boot loader
  FAT16 file system (hints score 5 of 5)
    Volume size 39.10 MiB (40994816 bytes, 20017 clusters of 2 KiB)
    Volume name "DellUtility"
Partition 2: 15.00 GiB (16105098240 bytes, 31455270 sectors from 80325, bootable)
  Type 0x07 (HPFS/NTFS)
  Windows NTLDR boot loader
  NTFS file system
    Volume size 15.00 GiB (16105097728 bytes, 31455269 sectors)
Partition 3: 20.00 GiB (21476206080 bytes, 41945715 sectors from 270630990)
  Type 0x83 (Linux)
  Ext3 file system
    UUID 9695AF89-CAE1-4671-83C9-A7C676369200 (DCE, v4)
    Last mounted at "/"
    Volume size 20 GiB (21474836480 bytes, 5242880 blocks of 4 KiB)
Partition 4: 114.0 GiB (122416842240 bytes, 239095395 sectors from 31535595)
  Type 0x0F (Win95 Ext'd (LBA))
  Partition 5: 40.00 GiB (42952379904 bytes, 83891367 sectors from 31535595+63)
    Type 0x07 (HPFS/NTFS)
    Windows NTLDR boot loader
    NTFS file system
      Volume size 40.00 GiB (42952376320 bytes, 83891360 sectors)
  Partition 6: 74.01 GiB (79464397824 bytes, 155203902 sectors from 115427025+63)
    Type 0x0B (Win95 FAT32)
    Windows NTLDR boot loader
    FAT32 file system (hints score 5 of 5)
      Volume size 73.99 GiB (79444934656 bytes, 2424467 clusters of 32 KiB)
      Volume name "DATA"

```

---

### Post by pastalavista on 2009-12-27
If you have the option to enter the Windows loader from the first splash screen before grub loads, (the same place you access the BIOS setup), try it and see if the sda5 drive will boot from there. Make sure there are no updates pending or system processes that haven't been completed and then reboot. Windows will lock the drive if it is in a transition state.

---

### Post by mrpaint on 2009-12-27
> **pastalavista said:**
> If you have the option to enter the Windows loader from the first splash screen (the same place you access the bios setup), try it and see if the sda5 drive will boot from there.
Actually, I modified the GRUB2 a little bit and it works fine. I can select to boot into Ubuntu or XP (and 2 other memtest options). Maybe you got me wrong, I can boot into XP but I can't read my files in /dev/sda5. Please wait, will boot into XP and take a screenshot for you guys (XP is extremly slow now... This will take time)

---

### Post by pastalavista on 2009-12-27
> **mrpaint said:**
> Actually, I modified the GRUB2 a little bit and it works fine. I can select to boot into Ubuntu or XP (and 2 other memtest options). Maybe you got me wrong, I can boot into XP but I can't read my files in /dev/sda5. Please wait, will boot into XP and take a screenshot for you guys (XP is extremly slow now... This will take time)

When you installed Windows 7 on sda5, it changed the MBR which is on sda2. Windows XP may still be the default boot, but Windows 7 is now in control of the MBR and it needs to be fixed before you'll be able to access it from another Windows OS. I don't think you'll be able to fix it from XP. Ubuntu sees it because it took control of the MBR with Grub and it isn't affected by the Windows system junk... I think. I'm not an expert.

Never mind me... I got confused as to what you're doing. Windows 7 ?? Where'd I get that?

---

### Post by mrpaint on 2009-12-27
> **pastalavista said:**
> When you installed Windows 7 on sda5, it changed the MBR which is on sda2. Windows XP may still be the default boot, but Windows 7 is now in control of the MBR and it needs to be fixed before you'll be able to access it from another Windows OS. I don't think you'll be able to fix it from XP. Ubuntu sees it because it took control of the MBR with Grub and it isn't affected by the Windows system junk... I think. I'm not an expert.
No, I installed Windows 7 on /dev/sda3 (which is now formated and used to install Ubuntu). I put the Windows Installation disc in and ran bootsec utility from that disc which recovered the default boot loader for Windows XP. Once again, current problem is Windows XP is unable to open the NTFS partition :(

And below is the screenshot from Windows XP. You can also see the desktop has been replaced with the ugly message regarding Active Desktop :( Quite exhausted with all this messy things

---

### Post by efflandt on 2009-12-27
How did your partitions end up in the wrong order?  That could be the problem.  I would rearrange them as follows, but the only thing I would trust to delete and recreate sda3, 5, 6, and 4 would be fdisk:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1963    15727635    7  HPFS/NTFS
/dev/**sda3**            1964       16846   119547697+   f  W95 Ext'd (LBA)
/dev/sda5            1964        7185    41945683+   7  HPFS/NTFS
/dev/sda6            7186       16846    77601951    b  W95 FAT32
/dev/**sda4**           16847       19457    20972857+  83  Linux
```Deleting and recreating partitions should not destroy any data as long as the partitions have the same exact start and end points, and you do NOT reformat.  Although, something else may have already corrupted something from having them in a different order than physical order.

---

### Post by pastalavista on 2009-12-27
Oh well, it all boils down to Windows is broken. Nothing new here. I would try to save as much as you can from the drive with Ubuntu and then reformat the whole extended (sda4) partition. Both drives are probably crawling with evil code.

---

### Post by SecretCode on 2009-12-27
Well ... I don't see anything wrong in the disktype output, although there may still be something there. It just seems like Windows has lost track of partition 5.

Can you run diskmgmt.msc from Windows and post a screenshot of the output?

Also, can you access sda5 from your Ubuntu installation? I can't see if you've mentioned this. Often Ubuntu can read an NTFS drive that Windows refuses to (but I would definitely mount it read-only - avoid writing to an NTFS drive with errors!).

---

### Post by mrpaint on 2009-12-29
Finally I managed to borrow my friend portable drive and copy all data in the NTFS partition. Actually, I was gonna copy everything and format the whole disk but after copy data in the NTFS partition, I formatted that partition and changed to use FAT32 (which I believe it is easier to read/write). I used Partition Magic and hell yeah, PM even updated the whole partition table and changed the order of partitions. I have to manually boot into Ubuntu since GRUB lost track but everything is fine now. Both Windows and Ubuntu work like charm!

Thank much for your help!

New Partitions table:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1963    15727635    7  HPFS/NTFS
/dev/sda3            1964       16846   119547697+   f  W95 Ext'd (LBA)
/dev/sda4           16847       19457    20972857+  83  Linux
/dev/sda5            1964        7185    41945683+   b  W95 FAT32
/dev/sda6            7186       16846    77601951    b  W95 FAT32

```

PS: Any one can help me changing the prefix for this thread to SOLVED?

---

### Post by SecretCode on 2009-12-29
Good stuff ... if in doubt, just reformat! *sledgehammer*

---

