---
title: "installed grub on wrong HD"
date: 2009-12-02
forum: General Help
---

### Post by Toast2120 on 2009-12-02
Hey recently did an install, but I had several hard drives plugged in at the same time. The filesystem was installed on one hard drive, while my boot was installed on another because I forgot to change the Grub location.

How do I reinstall the boot back on the filesystem?

---

### Post by Leppie on 2009-12-02
to install grub to the correct mbr:
```
$sudo grub-install /new/disk  ##change /new/disk to the disk you want to install grub to (e.g. /dev/sda)
```

to update your grub configuration:
```
$sudo update-grub
```

---

