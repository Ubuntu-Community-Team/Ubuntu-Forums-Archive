---
title: "Grub not seeing windows on either hardrive..."
date: 2006-05-13
forum: General Help
---

### Post by phlawed on 2006-05-13
I installed windows first on the hardrive, then ubuntu....in the past before breezy, the grub worked perfect and let me switch as i desired on boot. But, now, its nothing giving me anything to choose from but ubuntu. I have to hit esc on boot then options are only ubuntu. I have 2 hardrives, this one has ubuntu and windows, other has windows, but unbuntu wont see anything but ubunut? What happened to the boot loader? It use to be so simple.

---

### Post by aysiu on 2006-05-13
Can you paste this command into the terminal? ```
sudo fdisk -l
``` If something like this pops out: ```
Device Boot      Start         End      Blocks   Id  System
**/dev/hda1**   *           1        1911    15350076    7  HPFS/NTFS

``` Then most likely adding ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP
root            **(hd0,0)**
savedefault
makeactive
chainloader     +1
``` to the end of your /boot/grub/menu.lst file should fix this problem.

To edit your menu.lst, paste these commands in: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

---

### Post by phlawed on 2006-05-13
sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4911    39447576   83  Linux
/dev/hda2            4912        7296    19157512+   f  W95 Ext'd (LBA)
/dev/hda5            5100        7296    17647371    7  HPFS/NTFS
/dev/hda6            4912        5099     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19456   156280288+   7  HPFS/NTFS


i got this

---

### Post by phlawed on 2006-05-13
anything anyone?

---

### Post by aysiu on 2006-05-13
[QUOTE=phlawed]```

/dev/hda5            5100        7296    17647371    7  HPFS/NTFS
/dev/hdb1               1       19456   156280288+   7  HPFS/NTFS
```[/QUOTE] It looks as if you have two NTFS partitions--one on the fifth partition of your first hard drive, the other on the first partition of your second hard drive.

Do you know which one Windows is on?

---

### Post by dsokus on 2006-05-13
[QUOTE=phlawed]sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4911    39447576   83  Linux
/dev/hda2            4912        7296    19157512+   f  W95 Ext'd (LBA)
/dev/hda5            5100        7296    17647371    7  HPFS/NTFS
/dev/hda6            4912        5099     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19456   156280288+   7  HPFS/NTFS


i got this[/QUOTE]


Type   
```

sudo gedit /boot/grub/menu.lst
```

Then type your password and to the very end of the file add: 
```

title           Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1

title           Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

When you restart, there should be TWO "Windows XP" options - pick one of them and hope it works... If it doesn't, simply boot the other and that should, in theory, work... If not then it's probably Windows messing up!

To hide the "wrong" Windows XP, once you figured out which one worked, you can just put #'s in front of the lines corresponding to the "wrong" one in the grub menu.lst you just edited. I hope this helps!

---

