---
title: "I can't choose other OS in GRUB"
date: 2010-11-04
forum: General Help
---

### Post by utopcu on 2010-11-04
hi,
I am a new ubuntu user. Some problems about GRUB.

My pc:
Intel core i7 3.06 GHZ
G&#305;gabyte X58A-UD3R
9500GT
1 TB SATA2
4GB RAM

I HAVE A BIG PROBLEM. Starting from the beginnig. I installed Win7 Ultimate to my pc first. registered and updated bla bla.. then I divided into 3 partitions.

sudo fdisk -lu
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09da709b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   204799999   102296576   83  Linux
/dev/sda3       204802048  1064962047   430080000    7  HPFS/NTFS
/dev/sda4      1064962048  1953521663   444279808    7  HPFS/NTFS

```400 gb for win7
400gb for d
100gb for ubuntu 10.10

whatever i started to installing ubuntu and done it perfectly to my 100gb partition with format ext3.
when i reboot the computer grub list appears and i see windows 7 and ubuntu BUT I CAN NOT PUSH ANY BUTTON. IT AUTOMAT&#304;CALLY GOES TO UBUNTU WITHOUT LETTING ME CHANGE THE OS. IT COUNTS FROM 10 TO 0 AND OOPS. LINUX! DOWN ARROW OR ANY KEY DOESNT WORK IN GRUB MENU. PLEASE HELP ME.

---

### Post by kirkface8 on 2010-11-04
> **utopcu said:**
> whatever i started to installing ubuntu and done it perfectly to my 100gb partition with format ext3.
when i reboot the computer grub list appears and i see windows 7 and ubuntu BUT I CAN NOT PUSH ANY BUTTON. IT AUTOMAT&#304;CALLY GOES TO UBUNTU WITHOUT LETTING ME CHANGE THE OS. IT COUNTS FROM 10 TO 0 AND OOPS. LINUX! DOWN ARROW OR ANY KEY DOESNT WORK IN GRUB MENU. PLEASE HELP ME.


have you tried using a different keyboard?
possible a PS2 one

---

### Post by utopcu on 2010-11-04
i dont think it is because of keyboard. cause i can use it in bios screen but after bios in grub it doesnt work

---

### Post by Quackers on 2010-11-04
Bios screen and grub screen are at different stage of loading up. Another keyboard is worth trying imo.

---

### Post by utopcu on 2010-11-04
I will go buy a ps2 keyboard:) back in 30 minutes.

---

### Post by Quackers on 2010-11-04
Can't you borrow one for a while?

---

### Post by Hippytaff on 2010-11-04
> **Quackers said:**
> Can't you borrow one for a while?
 
haha - probably a good idea to try one before buying one :-)

---

