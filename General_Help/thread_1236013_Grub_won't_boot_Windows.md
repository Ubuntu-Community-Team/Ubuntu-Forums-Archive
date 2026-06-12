---
title: "Grub won't boot Windows"
date: 2009-08-09
forum: General Help
---

### Post by burpootus on 2009-08-09
I have a 3 physical hard drive system, drive #1 is Vista, drive #2 is data, and drive #3 is Ubuntu; a swap partition and a root partition. Here's the info:
sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba389052

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d1d818c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976769023   488383488    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52c2c7ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     4209029     2104483+  82  Linux swap / Solaris
/dev/sdc2         4209030   976768064   486279517+  83  Linux

I have the BIOS set to boot from disk #3 and this is where grub is installed. Recently, disk #1 failed and it was replaced under warranty. I set the BIOS to boot from that disk to simplify all of the upcoming reboots and reinstalled Vista. Now I've changed the BIOS back to booting from disk #3 and when I select Vista in grub, it returns a "BOOTMGR is missing, hit ctrl-alt-del to reboot". If I change the BIOS back to disk #1, Vista boots normally. Nothing has changed in the grub configuration and it boots Ubuntu normally when disk #3 is selected to boot in BIOS. Here's the code, which hasn't changed, to select Vista from the grub menu:

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Can anyone help me with this? Thanks

---

### Post by merlinus on 2009-08-09
If your vista disk is third in boot order, then change this

title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

to this

title        Windows Vista/Longhorn (loader)
rootnoverify        (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
savedefault
makeactive
chainloader    +1

If the vista hdd is second in boot order, change all instances of hd2 to hd1.

Also check /boot/grub/device.map so it agrees with hdd boot order.

---

### Post by burpootus on 2009-08-09
I guess I'm confused between "boot order" and what the BIOS recognizes as the order of the drives. Vista is /sda because it is plugged into SATA port 1, Ubuntu is /sdc because it is plugged into SATA port 3, etc.. I assume hd0 in grub is /sda. Are you saying hd0 is the first drive in the boot order instead of the first actual physical location? I always get confused with grub.

---

### Post by burpootus on 2009-08-09
Here's device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

---

### Post by merlinus on 2009-08-09
The boot order in bios is what determines the hd numbering for grub.  So the first hdd is hd0, second is hd1, and third is hd2 -- numbering for these things begins at 0 (zero).

Same for partitions.

According to device.map, sda is hd0, but it seems that hdd is not first in boot order.  Hence the confusion.

---

### Post by burpootus on 2009-08-10
That fixed the problem and I must give you a big thanks! A deep dark secret of grub has finally been revealed to me and it actually clicked in my mind for the first time! Boot order, not physical location...man, I wish I'd gotten that sooner.

---

### Post by merlinus on 2009-08-10
Glad you got it working.  Learning, as you know, is a life-long adventure.

Have fun...

---

