---
title: "grub problems finding windows xp pro"
date: 2009-07-17
forum: General Help
---

### Post by enoac on 2009-07-17
i have my computer set up to dual boot ubuntu 8.10 and windows xp pro sp2 but when i installed ubuntu for some reason when grub was installed it didn't find my windows partition. so i went it to manualy add windows to the grub loader so i went into the menu.lst file and added this to it ```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

but when i restart and try to boot into windows it says that it's missing something called BOOTMGR and tell me to press ctrl, alt, delete to restart my system. what is the easiest way to be able to boot into windows?

---

### Post by merlinus on 2009-07-17
Post results of

```
sudo fdisk -l
```

---

### Post by enoac on 2009-07-17
this is what it says ```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4c4c4c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2904    23326348+   7  HPFS/NTFS
/dev/sda2            2905        4865    15751732+   5  Extended
/dev/sda5            2905        4777    15044841   83  Linux
/dev/sda6            4778        4865      706828+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf55ff55f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4863    39062016    b  W95 FAT32

```

---

### Post by merlinus on 2009-07-17
Try changing this

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

to this

title           Microsoft Windows XP Professional
rootnoverify            (hd0,0)
savedefault
makeactive
chainloader     +1

Also make sure that sda is first in boot order in bios.

---

### Post by enoac on 2009-07-17
it still gives the same thing ```
BOOTMGR is missing
press CTRL+ALT+DEl to restart your computer
```

---

### Post by merlinus on 2009-07-17
Try supergrub to boot windows:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by akshay.sulakhe on 2009-07-17
no need to do so much trouble...bootmgr missing..is ur windows all right...check whether the boot files and ndltr files are present in ur windows drive....and if not install repair windows again...and its very easy to install grub again...

command to install grub

mkdir /temp
 mount /temp /dev/sda2
m assuming sda2 is ur linux partition

chroot /temp

grub-install hd0

done...and add windows which is already present in /boot/grub/menu.lst ..just uncomment them....

---

