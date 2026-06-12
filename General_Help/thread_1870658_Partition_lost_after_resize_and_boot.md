---
title: "Partition lost after resize and boot"
date: 2011-10-27
forum: General Help
---

### Post by Xades on 2011-10-27
[SIZE=2]While trying resize my Linux partition it became unallocated space and when restarted the computer it had the  grub rescue and in gparted it has [/SIZE]al of my dish as [SIZE=2]unallocated space but I can still access my windows vista drive thorough the LiveUSB. This is what I have so far using sfdisk.

[/SIZE]> ubuntu@ubuntu:~$ sudo sfdisk -luB

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 2046 does not have an msdos signature
Units = blocks of 1024 bytes, counting from 0

   Device Boot   Start       End    #blocks   Id  System
/dev/sda1      6144862+  8578709    2433847+  27  Hidden NTFS WinRE
/dev/sda2         1023   6144862-   6143839+   5  Extended
/dev/sda3   *  8586740  150105087  141518348    7  HPFS/NTFS/exFAT
/dev/sda4     150105088  156288352-   6183264+  17  Hidden HPFS/NTFS

Disk /dev/sdb: 1011 cylinders, 32 heads, 61 sectors/track
Units = blocks of 1024 bytes, counting from 0

   Device Boot   Start       End    #blocks   Id  System
/dev/sdb1   *       30+   986735     986705+   c  W95 FAT32 (LBA)
/dev/sdb2            0         -          0    0  Empty
/dev/sdb3            0         -          0    0  Empty
/dev/sdb4            0         -          0    0  Empty
ubuntu@ubuntu:~$ # sfdisk -d /dev/sdc > parts.txt
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# sfdisk -d /dev/sd1 > parts.tx
/dev/sd1: No such file or directory

sfdisk: cannot open /dev/sd1 for reading
root@ubuntu:/home/ubuntu# sfdisk -d /dev/sda > parts.tx
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 2046 does not have an msdos signature
root@ubuntu:/home/ubuntu# fixparts /dev/sdc
FixParts 0.8.0

Loading MBR data from /dev/sdc
Problem opening /dev/sdc for reading! Error is 123.

Unable to read MBR data from '/dev/sdc'! Exiting!

root@ubuntu:/home/ubuntu# fixparts /dev/sdd
FixParts 0.8.0

Loading MBR data from /dev/sdd
Problem opening /dev/sdd for reading! Error is 2.
The specified file does not exist!

Unable to read MBR data from '/dev/sdd'! Exiting!

root@ubuntu:/home/ubuntu# fixparts /dev/sda
FixParts 0.8.0

Loading MBR data from /dev/sda
MBR signature in logical partition invalid; read 0x0000, but should be 0xAA55
Segmentation fault (core dumped)
root@ubuntu:/home/ubuntu# fixparts 
FixParts 0.8.0
Type device filename, or press <Enter> to exit: sd1

Loading MBR data from sd1
Problem opening sd1 for reading! Error is 2.
The specified file does not exist!

Unable to read MBR data from 'sd1'! Exiting!
 [SIZE=2]

[/SIZE]

---

### Post by lightwarrior on 2011-10-27
It seems the lettering does not match anymore (number of partitions changed).

Try [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Which will repair the GRUB.

There are several How-to that will help you reinstall Grub, from LIVECD or USB boot.  This one should help.

---

### Post by oldfred on 2011-10-27
You do not show any Linux partitions???

Did you reformat somehow in resizing. Was sda3 the Linux partition and now it shows NTFS?

---

