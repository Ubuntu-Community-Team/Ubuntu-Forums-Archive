---
title: "Another dual boot problem post :("
date: 2009-10-03
forum: General Help
---

### Post by wideyes on 2009-10-03
Hi guys! I'm new to this forum and Ubuntu, so hello and thanks in advance! Please redirect/relocate this post if there is a better place for it...

I have installed Ubuntu 9.04 to my SD card on my asus eeepc 1000. I am dual-booting using GRUB, with XP/NTFS on my first HDD and  FAT32 on my second. Ubuntu boots fine under GRUB, but whenever I try to boot Windows I get an error 13 complaining about my executable. Here are my readings:

> 
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15743699     7871818+   7  HPFS/NTFS

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders, total 63045360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90599059

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    63039059    31519498+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 8017 MB, 8017412096 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006ec14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    14892254     7446096   83  Linux
/dev/sdc2        14892255    15647309      377527+   5  Extended
/dev/sdc5        14892318    15647309      377496   82  Linux swap / Solaris
According to this list, XP is installed on hd0, my fat32 drive is hd1 and my sd card with ubuntu is hd2. I'm not sure why grub would have listed an sd3 if none shows up in an fdisk query. My /boot/grub/menu.lst lists my Windows boot option as

> 
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1
For giggles I've tried changing the rootnoverify listing to each different HDD, but none work. Another note of interest: when I choose to boot ubuntu in GRUB a message says 'loading from hd0,0', which has me very confused. Isn't that my XP HDD? I am quite sure I have only loaded Ubuntu onto my SD card and have not touched my XP hard drive. I don't really understand what's going on. Can anybody clarify? Thanks again.

---

### Post by dcstar on 2009-10-03
> **wideyes said:**
> 
.........
According to this list, XP is installed on hd0, my fat32 drive is hd1 and my sd card with ubuntu is hd2. I'm not sure why grub would have listed an sd3 if none shows up in an fdisk query. My /boot/grub/menu.lst lists my Windows boot option as



Please do not "quote" code in your posts.

This is my entry for booting Windows off the first partiion on my first drive:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by wideyes on 2009-10-03
Thanks for the suggestion. I tried adding the "makeactive" command, but to no avail. Same error message.

---

### Post by wideyes on 2009-10-04
Solved!

I discovered you can use the 'geometry' command in grub to list information about each drive it has assigned. For some reason, it had made my flash card hd0 and my primary hd hd1. What confuses me is that this flies in the face of any other diagnostic I had run on my system. Can anybody explain why the two were flipped in grub?

The code that ended up working:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1
```Please give me your thoughts on the drive switch.

---

