---
title: "Trouble mounting drive"
date: 2009-10-21
forum: General Help
---

### Post by prem1er on 2009-10-21
I have a USB internal drive dock that acts as an enclosure for an internal drive.  I'm having trouble mounting it for some reason.  Normally, for flash (fat formatted) thumb drives I just do...

```
sudo mount /dev/... /media/usb
```

When I try with this drive I get..

```
prem1er@bubbles:/media/external$ sudo mount /dev/sdb .
mount: you must specify the filesystem type

```

Then I tried...

```
prem1er@bubbles:/media/external$ sudo mount -t ext3 /dev/sdb .
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Here is my fstab

```
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2456    19727788+  83  Linux
/dev/sda2            2457       91201   712844212+   5  Extended
/dev/sda5            2457       90720   708980548+  83  Linux
/dev/sda6           90721       91201     3863601   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9545

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          32      257008+  83  Linux
/dev/sdb2              33          95      506047+  82  Linux swap / Solaris
/dev/sdb3              96      121601   975996945   83  Linux

```

Any help? Thanks.

---

### Post by alphaniner on 2009-10-21
You need to specify the partition number:

```
sudo mount /dev/sdb1
```

It is possible that were using the whole device in the past (ie. /dev/sdb)* but in this case /dev/sdb has partitions and you need to choose one of them.  And you should always use partitions even if you only have one partition filling the entire device.

*That is, it is possible to format and mount the entire device ie. ```
mkfs.ext3 /dev/sdb
mount /dev/sdb /mount/point
```
...It's just not the way you're supposed to do it. :P

---

### Post by prem1er on 2009-10-21
Worked like a charm thank you very much.

---

