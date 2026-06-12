---
title: "Can't mount hard drive in Ubuntu"
date: 2010-08-12
forum: General Help
---

### Post by Bobscrachy on 2010-08-12
Why is it that now that I can use grub to access my vista drive I can't mount that vista drive in ubuntu. It is displayed in the disc utility. This is the error it gives when I try and mount. 

Before, when I wasn't able to boot the drive in grub it let me view it in ubuntu. Kind of fishy if you ask me. 

```

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed
```

---

### Post by dino99 on 2010-08-13
mountmanager is a nice tool to deal with partitions and devices, install it and set your prefs into 'system admin mountmanager, no need to tweak fstab or mtab

---

