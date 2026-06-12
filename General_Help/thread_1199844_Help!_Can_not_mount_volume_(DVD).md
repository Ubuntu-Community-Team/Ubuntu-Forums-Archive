---
title: "Help! Can not mount volume (DVD)"
date: 2009-06-29
forum: General Help
---

### Post by lobbert on 2009-06-29
[SIZE=2]Hi, my ubuntu system is  8.04..2.
When I tried to install the LabVIEW on my computer, (I try to use DVD to install.) it said "Cannot mount volume. invalid mount option when attempting to mount the volume 'ASLSP09MacLinux'."[/SIZE]
[SIZE=2]
My result for "sudo fdisk -l" is[/SIZE]

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94dfead2
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2            9143       24321   121925317+  83  Linux
/dev/sda3            8535        9142     4883760   82  Linux swap / Solaris
/dev/sda4              25        8534    68356575   83  Linux
Partition table entries are not in disk order
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024d7b
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

[SIZE=2]The result for "sudo cat /etc/fstab" is[/SIZE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ba5bd5a0-a5db-4b4c-8075-35f9a14163c7 /               xfs     relatime        0       1
# /dev/sda1
UUID=8bfe7efd-b0b4-47ef-ba75-dda7887f5bad /boot           ext2    relatime        0       2
# /dev/sdb1
UUID=a647a451-7692-41e8-9bd3-84e956ec9e67 /home           xfs     relatime        0       2
# /dev/sda4
UUID=d0cf0d29-374b-4e02-827b-1740719b985c /user           xfs     relatime        0       2
# /dev/sda3
UUID=2686784f-4301-4b5c-b235-db980204d1d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Could you help me to solve the problem?
It seems that my DVD rm can read out other disks except this one(LabVIEW). But this disk should be OK because another computer with SUSE system can read it.

Thanks a lot.

---

### Post by sese_k on 2009-07-24
Hi!

I have the same problem on Ubuntu 9.04. I tried then a manual mount of the drive with these commands:

```
$ sudo mount -t iso9660 /dev/sr0 /media/cdrom
$ sudo mount -t udf /dev/sr0 /media/cdrom
```In both cases I get the same error message:

```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```So I tried:
```
$ dmesg | tail
```This is the result:
```
[10968.396447] ISOFS: Unable to identify CD-ROM format.
[11035.652954] UDF-fs: No partition found (1)
```It seems, that when trying to launch with the ISO filesystem the format of the DVD can not be identified at all and with the UDF filesystem the DVD can be identified, but no partition is recognized. Is that correct? I'm pretty new to linux and just installed Ubuntu 3 days ago... So, as it does not work with both of the filesystems, is it possible, that I need to install an additional filesystem? On the DVD is the Linux distribution of LabVIEW as well as the MAC distribution, is it possible, that the DVD has a MAC specific filesystem, which is not known to my Ubuntu?

Hope someone can help with this...

Cheers,

Sebastian

---

### Post by sese_k on 2009-07-27
I posted what worked for me[COLOR=Red] [COLOR=Black][here]("http://ubuntuforums.org/showthread.php?t=1223545")[/COLOR][/COLOR].

Cheers,

Sebastian

---

