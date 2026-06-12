---
title: "Error 17: unable to mount selected partitions"
date: 2010-08-27
forum: General Help
---

### Post by archp2009 on 2010-08-27
I am currently getting error 17 (unable to mount selected partiton) for Ubuntu 9.04

This entry works:

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic 
root        (hd0,5) 
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet  splash 
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet

and this one for Windows XP

title        Windows XP (loader) 
rootnoverify    (hd0,0) 
savedefault 
makeactive 
chainloader    +1 

The non-working entry is for the Ubuntu as follows: 

title        Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda3) 
root        (hd0,2) 
kernel        /boot/vmlinuz-2.6.28-17-generic  root=UUID=69c058f1-beb7-4165-a8db-c052aacdf75b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic 
savedefault 
boot 

I have been booting into both the Mint 7 and Ubuntu 9 for a long time, but I started getting "Error 17: unable to mount selected partition" for the Ubuntu entry for the past few days. I don't know if hooking up a couple of optical drives would have thrown things off. Other than that the only thing I can think of is regular updates Any suggestions on how to get back into Ubuntu would be much appreciated.  Thanks in advance for any assistance.

Here is the display for gparted for my three SATA drives and one IDE hard disk. Apparently both Linux os's are on the first SATA drive.

arch@arch-desktop ~ $ sudo fdisk -l 
[sudo] password for arch: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x07510751 

  Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       35120   282101368+   7  HPFS/NTFS 
/dev/sda2           35126       36341     9767520   83  Linux 
/dev/sda3           36342       38043    13671315    5  Extended 
/dev/sda5           36342       37314     7815591   83  Linux 
/dev/sda6           37315       38043     5855661   83  Linux 

Disk /dev/sdb: 640.1 GB, 640135028736 bytes 
255 heads, 63 sectors/track, 77825 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x500b9b3f 

  Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1             988       16773   126801045    5  Extended 
/dev/sdb2           16774       77826   490400253    7  HPFS/NTFS 
/dev/sdb5             989        9912    71682030    7  HPFS/NTFS 
/dev/sdb6           11481       11989     4088511   82  Linux swap / Solaris 

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x5d7d47e1 

  Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1        3942    31662080    7  HPFS/NTFS 
/dev/sdc2            3943        7623    29567632+   7  HPFS/NTFS 
/dev/sdc3            7624       48441   327870585    7  HPFS/NTFS 
/dev/sdc4           48442      121601   587657700    7  HPFS/NTFS 

Disk /dev/sdd: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xba1a5abd

---

