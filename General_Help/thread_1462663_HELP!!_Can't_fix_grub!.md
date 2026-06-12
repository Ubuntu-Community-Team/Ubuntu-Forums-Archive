---
title: "HELP!! Can't fix grub!"
date: 2010-04-26
forum: General Help
---

### Post by qvyang on 2010-04-26
I am currently having a lot of trouble installing grub for my ubuntu 9.10.

I've been constantly getting all these errors:
```
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
```

I tried Super Grub Disk, EasyBCD but none of them worked.

I have the folling partitions:
/dev/sda1  linux swap 4GB
/dev/sda2  HPFS/NTFS  56GB ubuntu 9.10
/dev/sda3  HPFS/NTFS  windows 7 boot partition
/dev/sda4  HPFS/NTFS  173GB windows 7

Do anyone had this problem before? I have spent too much time on this now and I hope I don't need to reformat my ubuntu partition and going through the pain of reinstalling softwares and setups.

Thanks in advance!

---

### Post by zvacet on 2010-04-26
Reinstall grub following [this]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") guide.

---

