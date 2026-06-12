---
title: "NTFS drive wont mount"
date: 2009-11-23
forum: General Help
---

### Post by merlin371 on 2009-11-23
So i tried mounting the NTFS drive on my computer and it wont work this is the message i get.

> ntfs-3g: Failed to access volume '/dev/sdd1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)


even tho it says the drive isnt there when i do a fdisk -l i get this

> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d2db374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ce30765

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25176   202225196    7  HPFS/NTFS
/dev/sdb2   *       30401       60802   244191232    7  HPFS/NTFS
/dev/sdb3           25177       30400    41961780    5  Extended
/dev/sdb5           25177       30181    40202631   83  Linux
/dev/sdb6           30182       30400     1759086   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3872

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7649    61438976    7  HPFS/NTFS
/dev/sdc2            7650       15298    61440000    7  HPFS/NTFS
/dev/sdc3           15299       30515   122230552+   7  HPFS/NTFS

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62e94571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14594   117218304    7  HPFS/NTFS


now i should say when i was installing the os at first i wanted to put linux on a partition of the 250gb HD however ubuntu just didnt see it at all during install, the other 2 drives it sees them as just 1 big striped drive and it doesnt even work, as it show half of it being empty when it isnt.

Not sure what to do.

---

### Post by merlin371 on 2009-11-23
anyone? :D

---

### Post by RiceMonster on 2009-11-23
Looks like you're not typing the command right. You have to make a directory to mount it to first, then mount it.

try something like this:
```
sudo mkdir /mnt/drive/
sudo ntfs-3g /dev/sda1 /mnt/drive/
```

If you want it to mount on bootup, you can add it to /etc/fstab. Add a line that looks like this:
```
/dev/sda1  /mnt/drive/  ntfs-3g  defaults  0 0
```

Again, you have to create the directory first.

---

### Post by merlin371 on 2009-11-23
no the command is right, i can mount partitions from the 500gb HD no problem, is the other drives that wont mount.

---

### Post by intimatewipe on 2009-11-23
Hi Rice monster,
thanks bud you just solved by prob,see "list HD contents",I was getting syntax wrong and did not understand the mkdir bit,almost there,when I do  ls -al I get the folders in the ntfs partition but how can I list all folders sub-folders and files,
sorry for butting in and thank you many much:D,
if you could let me know so I can go to bed,I can't let it go:D

---

### Post by merlin371 on 2009-11-24
anyone has any ideas? i also tried gigolo and it says that the drive is busy, what i find weird is that only 3 HD have problems the 500GB never had an issue.

---

