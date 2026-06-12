---
title: "How to modify menu.lst on ubuntu 9 ( dual boot  )"
date: 2009-07-22
forum: General Help
---

### Post by alonefobia on 2009-07-22
I have just installed ubuntu on my PC, but now becouse of ubuntu can I can boot only ubuntu and Windows , can not boot anymore fedora :(
I have read comments here and tryed to modify the menu.ls on Ubuntu but it still doesnt work

here are the information that u may need 


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7228    58053208+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda3   *        7228        7253      204800   83  Linux
/dev/sda4            7254        9729    19888470    5  Extended
/dev/sda5            7254        9139    15149056   8e  Linux LVM
/dev/sda6            9140        9729     4739143+  83  Linux
tati@tati-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-07-21 19:18 20F03F6CF03F4776 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-07-21 19:18 55242f15-cd12-44bf-813a-d3984a13afcf -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-07-21 19:18 cedde70c-7958-4229-ace0-00206ef8c5cf -> ../../sda6
tati@tati-laptop:~$ gksudo gedit /boot/grub/menu.lst

---

