---
title: "stock in Grub rescue"
date: 2011-08-31
forum: General Help
---

### Post by Ashraf_2003 on 2011-08-31
Hi there, I have  ubuntu installed along side Win7, I like tring things so I tried app called smart boot manager (it was on my multiboot USB Stick) I played with some settings there like rescan partions and booted one of them it ran my Win7 when I restarted I had that Grub rescue  line.

I tried to solve this problem using system rescue cd, this is  what I see when I run fdisk -l 
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00253ad3

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?        2048   154626047    77312000    7  HPFS/NTFS/exFAT
/dev/sda2       154626048   427010047   136192000    7  HPFS/NTFS/exFAT
/dev/sda3       427010048   699394047   136192000    7  HPFS/NTFS/exFAT
/dev/sda4       699396094   976771071   138687489    5  Extended
/dev/sda5       699396096   976771071   138687488   83  Linux

Disk /dev/sdb: 8115 MB, 8115978240 bytes
250 heads, 62 sectors/track, 1022 cylinders, total 15851520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006a3band Gparted can't allocate my hdd, and I can't mount sda5 on terminal.

---

### Post by seawolf167 on 2011-08-31
Duplicate post - [see here]("http://ubuntuforums.org/showthread.php?t=1836771")

---

