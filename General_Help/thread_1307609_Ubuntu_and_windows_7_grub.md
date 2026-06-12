---
title: "Ubuntu and windows 7 grub"
date: 2009-10-31
forum: General Help
---

### Post by LordOrange on 2009-10-31
I've been trying to fix my grub settings for 3 days now after installing windows 7 on my second drive, which used to boot to windows XP.

I have two drives on my system, a 320gb and a 80GB. The Windows is installed on the 80 and my Ubuntu and other storage partitions is on my 320.

Right now if I start with the 80 set to first drive in my BIOS priority list it boots straight into Windows. If I have my 80 in priority, it loads the brub but gives me an NTLDR error with the windows option.

I've tried every setting I can find for my grub settings with the windows drive but nothing seems to work. Bellow is what i get from 'fdisk -l' and my windows setting from my grub menu.lst file. If any one could help it would be great.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12a5c2d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a17f530

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29252   234966658+   7  HPFS/NTFS
/dev/sdb2           31681       38913    58099072+   5  Extended
/dev/sdb3           29253       31680    19502910   83  Linux
/dev/sdb5           31681       38799    57183336   83  Linux
/dev/sdb6           38800       38913      915673+  82  Linux swap / Solaris




title        Microsoft Windows XP Professional
root    (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader   +1

---

