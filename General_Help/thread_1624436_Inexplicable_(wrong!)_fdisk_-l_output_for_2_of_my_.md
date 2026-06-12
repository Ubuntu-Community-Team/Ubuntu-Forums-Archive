---
title: "Inexplicable (wrong!) fdisk -l output for 2 of my flash drives"
date: 2010-11-17
forum: General Help
---

### Post by qu3rY on 2010-11-17
Every time I try to format a USB flash drive to prepare it for installing a linux OS, my it ****s up! I can't tell you _exactly_ what I do to **** it up, but I can tell you that I have beeing using fdisk to partition two primary partitions, the first one being +10M boot, the second fills up the rest of the 4GB. Yeah, these are both 4GB flash drives when I bought them...
```

Disk /dev/sdb: 16 MB, 16777216 bytes
1 heads, 32 sectors/track, 1024 cylinders
Units = cylinders of 32 * 512 = 16384 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 4047 MB, 4047502848 bytes
125 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1020     3952469   83  Linux

```I keep trying to create a partition on /dev/sdb
/dev/sdc _looks_ ok from fdisk -l, but when CentOS (yes, I'm trying to get back into Debian...) automagically mounts it, the normal "3.8 GB Removable Volume" link appears on the desktop, but only 13.6 MB is available on the disk. I have confirmed this in Windows XP.

I have an idea: Get a functional 4 GB flash drive /dev/sdd and run these commands:
```

dd if=/dev/sdd of=/dev/sdb
dd if=/dev/sdd of=/dev/sdc

```It would overwrite the MBR, or boot sector, or whatever; everything. I have no idea what metadata is actually on a flash drive, but if I didn't do anything to physically damage the disk, then something like the MBR must be corrupted. Does anyone know what's wrong?

---

### Post by qu3rY on 2010-11-17
In case you guys have only Ubuntu solutions for me, I have replaced CentOS 5 with Ubuntu 10.10.

---

### Post by qu3rY on 2010-11-18
So no one knows why in the world fdisk would report a 4 GB flash drive to be 16 MBs?

---

### Post by Rubi1200 on 2010-11-18
There could be a number of possible reasons.

First things first:
post the output of ```
sudo fdisk -lu
```Thanks.

EDIT: you may also want to take a look here for other options: [http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

---

### Post by viralmeme on 2010-11-18
> **qu3rY said:**
> Every time I try to format a USB flash drive to prepare it for installing a linux OS, my it ****s up

I had that happen on a USB drive after a number of formats. Fdisk kept reporting multiple non-existant partitions etc. You could try DDing it and/or running the HP USB utility on it.

$dd if=/dev/zero of=/dev/path.to.usb.device bs=1M

[HP Drive Key Boot Utility]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839")

---

