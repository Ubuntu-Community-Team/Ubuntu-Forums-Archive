---
title: "Problems with ubuntu on dell dimension 9100 with SATA"
date: 2006-04-19
forum: General Help
---

### Post by mwolfe on 2006-04-19
Alright i have a dell 9100 with a p4 model 820.
It came with a 160gb SATA drive. I then installed a IDE controller card (raid capable) and installed 1 160gb ide drive. Now i could care less to utilize raid or anything here, i just want my two drives to work (independantly) and be able to boot either windows or linux. 

There are 4 settings
RAID Autodetect/AHCI, RAID Autodected ATA, Raid Only, and Combination
mode.
Ubuntu only works when i have the bios setting on Raid only. Windows will work under Raid Only except that it won't boot from grub, i get an error (even though this was setup automatically when installing ubuntu, and i have tried other combinations manually and nothing has worked)

The first two settings seem to be pretty much useless with my ide drive installed.. the comp just freezes irregardless of what i do. without the ide drive installed i believe they both work but its been a long time since i tried.
If i run Raid Only setting, I can boot linux (if linux was installed while under this setting) and both my hard drives work and everything is find and dandy.. Except, in order to boot windows i have to change the boot priority and put the SATA drive which is what has windows on it, in front of the IDE drive. 

here is my grub.conf
```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hde1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

and here is my fdisk -l output
```
mwolfe@wolfedell:/boot/grub$ sudo fdisk -l

Disk /dev/hde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        3986    32017513+  83  Linux
/dev/hde2   *        3987        5810    14651280   83  Linux
/dev/hde3            5811       19929   113410867+   b  W95 FAT32

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4189    33599947+   7  HPFS/NTFS
/dev/sda3            4190       19013   119073780    f  W95 Ext'd (LBA)
/dev/sda4           19014       19452     3526267+  db  CP/M / CTOS / ...
/dev/sda5            4190        7410    25872651    7  HPFS/NTFS
/dev/sda6            7411        9794    19149448+   b  W95 FAT32
/dev/sda7            9795        9996     1622533+  82  Linux swap / Solaris
/dev/sda8            9997       19013    72429021    b  W95 FAT32

```

Now that isnt a big deal but its kind of a pain especially since my wife uses the computer and she's not big on linux yet. 

So here is the alternative, i can install linux in combination mode and both windows and linux can boot from grub.. but linux then doesnt recognize my sata drives, yet windows recognizes both.. 


Any ideas, i've honestly tried everything and i can't seem to get both booting from grub.. Even if i could somehow boot grub from the windows loader, i think i've seen that done before..

---

