---
title: "Grub booting ubuntu and Xp"
date: 2009-07-15
forum: General Help
---

### Post by alucito on 2009-07-15
Hi, well this is my problem, originally i had vista on my computer, with the recovery section, I replaced vista with xp, but i left the vista recovery just in case.
right now i wanted to add ubuntu as well, but i had a little problem booting xp.

here is my fdisk -l results 


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c195c19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       28554   229351972+   f  W95 Ext'd (LBA)
/dev/sda2   *       29088       30401    10554705    7  HPFS/NTFS
/dev/sda5               2       12749   102398278+   7  HPFS/NTFS
/dev/sda6           12750       28554   126953631   83  Linux


and this is my menu.lst result (only important stuff)



title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic OLD
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) OLD
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows Xp
root (hd0,4)
savedefault
makeactive
chainloader +1

title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1



i would like to be able to boot both, xp, and ubuntu.
Please tell me what do i have to change, whats my mistake.
right now i dont have the xp iso, or cd.
please try to be as clear as possible cuz im kinda new on ubuntu.
Thank everybody in advance.

---

