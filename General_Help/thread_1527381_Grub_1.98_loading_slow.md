---
title: "Grub 1.98 loading slow"
date: 2010-07-09
forum: General Help
---

### Post by jangozo on 2010-07-09
Hello,

I've got a dual boot 64 bit laptop with Win 7 and Ubuntu 10.4. Whenever I boot or reboot it I have to wait until Grub loads while there is nothing but black screen showing with the little cursor underscore ( _ ) appearing.

This is the disk setup at the moment after doing an fdisk -l:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       27453   205107366+   7  HPFS/NTFS
/dev/sda4           27453       30402    23689217    5  Extended
/dev/sda5           27453       30274    22660096   83  Linux
/dev/sda6           30274       30402     1028096   82  Linux swap / Solaris
```In addition, once I choose the OS to boot, I have to wait on a blank screen again when booting either Win 7 or Ubuntu. The wait on every blank screen is of around 5 seconds.

How can I fix this?

Thanks

---

