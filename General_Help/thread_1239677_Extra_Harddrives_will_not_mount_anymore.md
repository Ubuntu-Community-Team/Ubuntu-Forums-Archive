---
title: "Extra Harddrives will not mount anymore"
date: 2009-08-13
forum: General Help
---

### Post by ssanders4917 on 2009-08-13
I have two hardrives separate from my file system that i use for media and what not. They have mounted fine until today. I now get: "Invalid mount option when attempting to mount the volume 'SHARE'". I have tried a restart but cannot get them to work. The problem did not start until i did a system update today. Any help would be great. I need to get in them.

---

### Post by ssanders4917 on 2009-08-14
bump

---

### Post by khelben1979 on 2009-08-14
Do you try to mount them using the sudo command?

How long have they been working?

---

### Post by matthewbpt on 2009-08-14
Are they automounted on startup or do you mount them yourself?

Give us the output of

```
sudo fdisk -l
```

and

```
cat /etc/fstab
```

---

### Post by ssanders4917 on 2009-08-14
Yes I mount them and they have been working for a year now.

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fef9fef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c069c06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9353    75127941   83  Linux
/dev/sdb2            9354        9729     3020220    5  Extended
/dev/sdb5            9354        9729     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc6e09f94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20672   156280288+   7  HPFS/NTFS

-----------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ee65587-131a-49f2-b7eb-6b813b6dfbfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=df98efed-7a1b-4b07-a857-5c1823250378 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ssanders4917 on 2009-08-17
anyone? I still can't get into my drives

---

### Post by khelben1979 on 2009-08-17
Have you tried connecting it to other usb ports? Also, have you checked the usb cable to see if anything is wrong there?

---

### Post by michy99 on 2009-08-17
Try```
sudo lsusb
``` and then see if they are mounted.

---

### Post by ssanders4917 on 2009-08-17
They are SATA drives connected to MOBO

---

### Post by ssanders4917 on 2009-08-17
no dice

---

### Post by michy99 on 2009-08-17
> **ssanders4917 said:**
> They are SATA drives connected to MOBO

Sorry, I read 'Extra' as 'External.'

---

### Post by ssanders4917 on 2009-08-17
Here is a screen shot of error message.

---

### Post by ssanders4917 on 2009-08-17
I have also tried connecting the drives to different ports on the mobo; I am not sure if that would even make a difference and it didn't

---

### Post by ssanders4917 on 2009-08-17
not sure if this helps

---

### Post by ssanders4917 on 2009-08-17
I fixed the problem. I downloaded storage device manager and ran its configuration tool and I was able to mount the drives. I'll pat myself on the back

---

