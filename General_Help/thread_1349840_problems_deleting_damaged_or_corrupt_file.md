---
title: "problems deleting damaged or corrupt file"
date: 2009-12-08
forum: General Help
---

### Post by yanvolking on 2009-12-08
Hello Community,

I have somehow got a corrupt or damaged file in my backup directory:

home_desktop_tar_bkp.tar.bz2

I try to use sudo rm -f on it but this is what I get:

yan@yan-desktop:/media/Iomega HDD/ALL/backups$ sudo rm -f /home_desktop_tar_bkp.tar.bz2
yan@yan-desktop:/media/Iomega HDD/ALL/backups$ ls -al
ls: cannot access home_desktop_tar_bkp.tar.bz2: Input/output error
total 8
drwx------ 1 yan yan 4096 2009-12-08 23:22 .
drwx------ 1 yan yan 4096 2009-12-04 23:11 ..
-????????? ? ?   ?      ?                ? home_desktop_tar_bkp.tar.bz2
yan@yan-desktop:/media/Iomega HDD/ALL/backups$ 

Is there any way I can just blast this file off my HDD?

Thanks

Yan

---

### Post by 3Miro on 2009-12-08
Look around on how to force a disk scan, then try to reboot and scan the disk. If the file is corrupted, then the system might not know what exactly this file is. Another option is to boot from the live CD and delete it from there, but this an extreme case.

You can also try different file managers (nautilus, command line, dolphin and there are others, Google on Linux file managers).

---

### Post by joes7 on 2009-12-11
Some programs will let you delete those files.

---

