---
title: "After reformating, &quot;Properties&quot; disagrees with fdisk"
date: 2009-08-19
forum: General Help
---

### Post by nmaster on 2009-08-19
I have an external hard drive that was FAT32.  I used mkntfs to reformat it.  However, take a look at the code (/dev/sdc1) versus the screenshot (particularly the underlined bit).  The terminal still shows the device as FAT but the GUI shows NTFS.  mkntfs didn't return any errors while formating and even my father's XP desktop reads the device as NTFS.

Why the discrepancy?



```

neal@neal-laptop:~$ sudo fdisk -l
[sudo] password for neal: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x149f149f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17957   144239571    5  Extended
/dev/sda2           17958       19457    12048750    7  HPFS/NTFS
/dev/sda5               1       17507   140624914+  83  Linux
/dev/sda6           17508       17957     3614593+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)


```

---

### Post by nmaster on 2009-08-19
Just to let you know, the reason I reformatted was so that I don't have to deal with the 4.0GB file limit on FAT.  I want to use PartImage to make an image of my root partition but I know that this image file will be greater than 4GB.  I don't want to waste time trying to use PartImage until I know that the drive is actually NTFS.  Thanks all.

---

### Post by nmaster on 2009-08-20
bump.

---

### Post by nmaster on 2009-08-20
also, which one is correct?

---

### Post by nmaster on 2009-08-20
anyone....?

---

### Post by nmaster on 2009-08-23
well, thanks to anyone who at least read this.  i'll go ahead and try moving a 4+GB file and see what happens tomorrow.  i'll post back in case this happens to anyone else.

---

### Post by nmaster on 2009-09-12
> **neal.m.master said:**
> well, thanks to anyone who at least read this.  i'll go ahead and try moving a 4+GB file and see what happens tomorrow.  i'll post back in case this happens to anyone else.

i was able to move a 13GB file to the drive so its definitely NTFS.  can anyone explain why the terminal says the system is FAT32?!!!

---

