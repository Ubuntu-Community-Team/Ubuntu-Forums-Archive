---
title: "2 HD's, XP boot from Grub - Missing NTLDR, Bios change to start XP HD works fine."
date: 2009-10-31
forum: General Help
---

### Post by iMisspell on 2009-10-31
Computer has three sata hard-drives..
First drive has XP installed (single partition)
Second is storage NTFS (single partition)
Third has Ubuntu 9.04 installed (single partition)

Ubuntu boots fine through Grub, but XP will kick up the "*Missing NTLDR error*" if tried to booting though grub. If i change the boot disc in the Bios to boot the XP drive first, XP loads fine, no errors.

Heres what i did...
XP was installed first (over a year) on one hard-drive and using the second HD for storage. Added a third HD to install Ubuntu.
During the Ubuntu install process i selected the newly add HD, set that hard-drive as the boot/Master.
Cant rember when i did this, eather before installing Ubuntu or during the restart after ubuntu was installed, i change the boot/first hard-drive in the bios to the Ubuntu drive.

When the bios is set to run the Ubuntu drive first, the Grub loads and Ubuntu will load up fine, but if i try to load XP from the Grub i get the NTLDR error message. If i go to the bios and change the start/boot drive to the XP drive, XP will load fine (no grub).

Heres some info, _XP is installed on Disk /dev/sdb: 82.3 GB_

sudo fdisk -l 
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6cc2ac7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfc7dfc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8212    65962858+   7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031648

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       76507   614542446   83  Linux
/dev/sdc2           76508       77825    10586835    5  Extended
/dev/sdc5           76508       77825    10586803+  82  Linux swap / Solaris
```



/boot/grub/menu.lst
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		174978a2-2892-41c7-86b7-b27c837c7772
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=174978a2-2892-41c7-86b7-b27c837c7772 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		174978a2-2892-41c7-86b7-b27c837c7772
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=174978a2-2892-41c7-86b7-b27c837c7772 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		174978a2-2892-41c7-86b7-b27c837c7772
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=174978a2-2892-41c7-86b7-b27c837c7772 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		174978a2-2892-41c7-86b7-b27c837c7772
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=174978a2-2892-41c7-86b7-b27c837c7772 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		174978a2-2892-41c7-86b7-b27c837c7772
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Can someone give me a little guidance on the correct settings for (and explanation would be good too, if you have the time ;) ):
```
title		Windows NT/2000/XP (loader)
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Why is this twice (searching the net seams like its standard) ?
```
map		(hd0) (hd1)
map		(hd1) (hd0)
```

thanks...

[edit]
Working now, check next post for info...
_

---

### Post by iMisspell on 2009-11-01
Got it working...
There was an important (i think) peice of information which i forgot to mention in the first post (two bottles of Heineken will do that to me :( ).
The m/b has two sata and i just added a card which has an additional four.

Before installing Ubuntu, the machine had two drives both working off the m/b's sata, when i added the card, i moved the storage drive to the card and hook up the new hard-drive for ubuntu to the m/b.

Last night i switched the storage drive and the ubuntu drive (ubuntu is now hooked to card, storage is back to m/b) and changed the bios to boot off the sata-card.

Restarted the machine, grub loaded fine and ubuntu loaded fine. Did a re-start and tried XP, Xp loaded fine *though grub*. I would like to know why, but its working so i'll except that :)
Mahine has been restarted a few times since these changes took place, and its working fine.

The only thing i change was to physically switching the two drives.

Heres the current info:

sudo fdisk -l
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76507   614542446   83  Linux
/dev/sda2           76508       77825    10586835    5  Extended
/dev/sda5           76508       77825    10586803+  82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8212    65962858+   7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48641   390708801    7  HPFS/NTFS
```

My last testing options...
Both (hd2,0) and (hd1,0) will load XP with out a problem (???) .
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader error 1,0 )
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Windows NT/2000/XP (1,0 - root)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Windows NT/2000/XP (2,0 - root )
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```


Thought i would post this incase it can help someone else.

_

---

