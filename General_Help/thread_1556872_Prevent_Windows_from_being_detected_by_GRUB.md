---
title: "Prevent Windows from being detected by GRUB"
date: 2010-08-20
forum: General Help
---

### Post by M4he on 2010-08-20
I've got 2 HDDs. Ubuntu 10.04 is installed on the first and Windows on the second. But Windows is only on a small partition for special cases. Therefore I don't want that Windows to be included in GRUB whenever the kernel is updated or whenever I run update-grub. If I really want to start Windows, I am able to do so via a menu from BIOS.

Is it possible to permanently exclude Windows from grub or disable GRUB's autosearching for other operating systems?

Thanks in advance!

---

### Post by Elfy on 2010-08-20
Yes it is possible 

Either add this to /etc/default/grub 

GRUB_DISABLE_OS_PROBER=true

Or run ```
sudo chmod a-x /etc/grub.d/30_os-prober
``` to stop os-prober.

After either run ```
sudo update-grub
```

---

### Post by M4he on 2010-08-20
That works like a charm, thanks very much!

Solved.

---

