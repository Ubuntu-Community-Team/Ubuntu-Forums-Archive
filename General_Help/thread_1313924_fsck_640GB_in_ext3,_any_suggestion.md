---
title: "fsck 640GB in ext3, any suggestion?"
date: 2009-11-04
forum: General Help
---

### Post by sakurazukamori on 2009-11-04
Hi everybody : D

Recently my external hard disk assumed a weird behaviour, and now it's becoming more and more dangerous, like I can navigate by command line through my folders and open single files, but can't do the same by nautilus or other graphic tool.

So... I've got to fsck it!!!

But...

```
e2fsck -yv /dev/sdb1
```

Takes soooo much time also sometimes it does simply nothing (no activity on the disk, verbose mode tells nothing), and since it's a 640GB disk...
I guess that checking all inode will be a kind of a time wasting :-\

Problem is that I can't do that with my laptop (I need it as a laptop, so sticked to my hard disk at home doesn't sound like mobile in my opinion).


Any suggestion, or a trick, to speed up this check? :-/


I'll stick some useful output:

```
$mount

/dev/sdb1 on /media/2081fe77-c747-4fba-ae99-026a919336e6 type ext3 (rw,nosuid,nodev,uhelper=devkit)

```

```
$dmesg | tail


[120977.991474] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[120977.993731] EXT3 FS on sdb1, internal journal
[120977.993741] EXT3-fs: recovery complete.
[120978.013748] EXT3-fs: mounted filesystem with writeback data mode.
```

```
$sudo fdisk -l

Disco /dev/sdb: 640.1 GB, 640135028736 byte
255 testine, 63 settori/tracce, 77825 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x7d413b3b

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux

```

---

