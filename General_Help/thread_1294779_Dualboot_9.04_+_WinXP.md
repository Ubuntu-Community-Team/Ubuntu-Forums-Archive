---
title: "Dualboot 9.04 + WinXP"
date: 2009-10-18
forum: General Help
---

### Post by gus_zernial on 2009-10-18
I have a box with two Kubuntu 9.04 installations, one on a solid state disk (SSD) and one on a linux two-disk RAID, and a WinXP installation 
on a partition on one of the RAID disks. The BIOS boots the SSD first; 
(hd2) or /dev/sdc; see command output below. From there, grub will boot either of the two Kubuntu installations successfully. 

Grub initially booted the WinXP partition successfully as well, but now that's stopped working, and on an attempt to boot the WinXP installation,
grub gives an "invalid partition" message. It can be seen from the command output below that the WinXP root is specified to the (hd0,2) partition, which I think is right and which worked before. I can't think of anything relevant that I've changed.

Can someone see something wrong with my config, or give me ideas to diagnose and/or fix the problem?

$ cat menu.lst

## ## End Default Options ##

title           Ubuntu jaunty (development branch), kernel 2.6.28.9r2
root            (hd0,0)                                              
kernel          /vmlinuz-2.6.28.9r2 root=/dev/md1 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M                                                                                                       
initrd          /initrd.img-2.6.28.9r2                                                                   

title           Ubuntu jaunty (development branch), kernel 2.6.28.9r2 (recovery mode)
root            (hd0,0)                                                              
kernel          /vmlinuz-2.6.28.9r2 root=/dev/md1 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd          /initrd.img-2.6.28.9r2                                                               

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            c37aaed5-464f-4487-8a93-01ecacc4ec12 
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c37aaed5-464f-4487-8a93-01ecacc4ec12 ro quiet splash                                                                                                    
initrd          /boot/initrd.img-2.6.28-11-generic                                                       
quiet                                                                                                    

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            c37aaed5-464f-4487-8a93-01ecacc4ec12                 
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c37aaed5-464f-4487-8a93-01ecacc4ec12 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            c37aaed5-464f-4487-8a93-01ecacc4ec12
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows XP Professional
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1

$ cat device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000efd49                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   fd  Linux raid autodetect
/dev/sda2            6080       54953   392580405    5  Extended             
/dev/sda3   *       54954       60800    46966027+   7  HPFS/NTFS
/dev/sda5            6080        6322     1951866   82  Linux swap / Solaris
/dev/sda6            6323       54953   390628476   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000558d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   fd  Linux raid autodetect
/dev/sdb2            6080       54953   392580405    5  Extended
/dev/sdb5            6080        6322     1951866   82  Linux swap / Solaris
/dev/sdb6            6323       54953   390628476   fd  Linux raid autodetect

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002bda5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7460    59922418+  83  Linux
/dev/sdc2            7461        7783     2594497+   5  Extended
/dev/sdc5            7461        7783     2594466   82  Linux swap / Solaris

---

### Post by -Zeus- on 2009-10-19
First weird thing I see is the "rootnoverify" option in Win XP.  Maybe try putting that back to "root"?

---

### Post by P4man on 2009-10-19
rootnoverify is correct for XP
However, Ive never known XP was able to boot from anything but the first partition

---

### Post by -Zeus- on 2009-10-19
good point, and I didn't know about rootnoverify.

---

