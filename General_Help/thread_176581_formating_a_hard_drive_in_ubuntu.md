---
title: "formating a hard drive in ubuntu"
date: 2006-05-15
forum: General Help
---

### Post by tomslopez on 2006-05-15
Ok I have a 279gb external hard drive which I want to format to be able to read and write with ubuntu and windows. First how do I format it in ubuntu? and what type of format can I use to do this?

---

### Post by aysiu on 2006-05-15
As long as it's not NTFS, you're good.

If it's FAT32, FAT16, or Ext3, you'll be fine.

If you're not sure what it is, plug it in and paste this command into the terminal: ```
sudo fdisk -l
```

---

### Post by tomslopez on 2006-05-15
I don't see where its suppose to say what type it is, it says how many gb it has and all but it doesn't say the type.

---

### Post by aysiu on 2006-05-15
[QUOTE=tomslopez]I don't see where its suppose to say what type it is, it says how many gb it has and all but it doesn't say the type.[/QUOTE] When I plug my USB external hard drive in, this is what I get: ```
sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  **HPFS/NTFS**
/dev/hda2            1912       19457   140938245    5  Extended
/dev/hda5            1912       18174   130632516   83  **Linux**
/dev/hda6           18175       18295      971901   82  **Linux swap / Solaris**
/dev/hda7           18296       19457     9333733+  83  **Linux**

[i]Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       19929   160079661   83  **Linux**[/i]
``` The types are in bold. My external hard drive is in italics. Unfortunately, for Ext3, they just call it *Linux*, but for FAT or NTFS, you'll definitely see *FAT* or *NTFS*.

---

### Post by tomslopez on 2006-05-15
here is how mine looks like, I just tried to format my external hard drive as it says in the wiki, but I don't see how to make it accessible.

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

the disk with the 300 gb is my external.

---

### Post by aysiu on 2006-05-15
[QUOTE=tomslopez]here is how mine looks like, I just tried to format my external hard drive as it says in the wiki, but I don't see how to make it accessible.
```
Disk /dev/sda doesn't contain a valid partition table
```[/QUOTE] It doesn't look as if the formatting was successful. What did you use to format it? GParted? Some command-line tool?

---

### Post by Gomek on 2006-05-15
Try:

```
sudo -s
cfdisk /dev/sda
```

Create a partition and change it to type 0b.  Write the changes to disk and exit.  Now:

```
mkdosfs -F 32 /dev/sda1
```

Hopefully this accomplishes what you're after.

---

### Post by tomslopez on 2006-05-15
when I do cfdisk /dev/sda, the terminal window turns blak and it says FATAL ERROR: Cannot open disk drive

---

### Post by Slim Odds on 2006-05-15
With which version of Windows do you plan to "share" this drive?

from [http://support.microsoft.com/kb/q154997/](http://support.microsoft.com/kb/q154997/)

> NOTE: Microsoft Windows 2000 only supports FAT32 partitions up to a size of 32 GB.

I don't know what cfdisk is, but fdisk should work fine.

Just remember that partitioning and formatting are two different things.

---

### Post by tomslopez on 2006-05-15
With windows xp.

---

