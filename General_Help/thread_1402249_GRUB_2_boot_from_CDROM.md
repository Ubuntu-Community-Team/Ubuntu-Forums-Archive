---
title: "GRUB 2 boot from CDROM"
date: 2010-02-08
forum: General Help
---

### Post by crypticfoe on 2010-02-08
What code would i run to boot a cdrom from the old menu.lst? I used to use: 

    title    CDROM
root    (hd0,0)
kernel    /boot/grub/memdisk.bin
initrd    /boot/grub/sbootmgr.dsk

Would i still use this code but saved as a file name of some sort under /etc/grub.d/ ?

---

