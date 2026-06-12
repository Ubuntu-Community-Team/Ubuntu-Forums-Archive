---
title: "Auto Mounting HDs - 5th disk not recognised"
date: 2010-01-13
forum: General Help
---

### Post by NEUR0M4NCER on 2010-01-13
Another drive, another issue with mounting.

I thought I'd format my new 2tb drive to ext4, so did that, created a mount point, chown'd it, edited fstab, and now it gives me this:
```

neur0m4ncer@box:~$ sudo mount -a
mount: special device /dev/sde1 does not exist
```
What have I done wrong? Is there some special requirement for ext4 that I should have checked on first - and please tell me I haven't just hosed £120 worth of new HD... please!

Oh - here's my current non-working fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=f0115bc3-7656-47c9-84c5-6f417231fa7d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0
/dev/sda1	/storage-2	auto	defaults	0	0
/dev/sdb1	/		ext3	defaults	0	0
/dev/sdc1       /storage-1      ext3    defaults        0       0
/dev/sdd1       /storage-0      ext3    defaults        0       0
/dev/sde1       /storage-3      ext4    defaults        0       0

```
... and sudo fdisk -l
```

neur0m4ncer@box:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c136ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14105   113298381   83  Linux
/dev/sdb2   *       14106       18707    36965565    7  HPFS/NTFS
/dev/sdb3           18708       19457     6024343+  82  Linux swap / Solaris

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073bed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004b15b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux

```

---

### Post by NEUR0M4NCER on 2010-01-13
... and rather worryingly, I've just noticed that GParted doesn't see that there's a (sde) disk there any more - that's not right, is it? It formatted the thing just fine an hour and a half ago.

---

### Post by NEUR0M4NCER on 2010-01-13
*FACEPALM*

The cheap molex power splitter has a loose connection...

note to self: always check the HARDWARE first!

---

### Post by NEUR0M4NCER on 2010-01-13
Nope - that wasn't it. I've now removed the IDE drive as I thought that might have caused an issue, if only by having too many power draws on the PSU... so now I can get intermittent access to the (now) fourth drive - but it will work for a while, then suddenly tell me that it's now 'Read Only'.

Any ideas?


**** edit ****

and then it stops showing up in fdisk -l again. Grrr.

---

