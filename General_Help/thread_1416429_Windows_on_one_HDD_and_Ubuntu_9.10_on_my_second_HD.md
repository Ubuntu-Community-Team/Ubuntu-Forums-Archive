---
title: "Windows on one HDD and Ubuntu 9.10 on my second HDD"
date: 2010-02-26
forum: General Help
---

### Post by scumboss on 2010-02-26
Hi All

I have Windows on my primary hard disk and I've just installed Ubuntu 9.10 on my secondary hard disk.  When I boot my PC Windows just loads.  I want to have a menu so I can select either Windows or Ubuntu, any ideas?

Thanks

---

### Post by mick222 on 2010-02-26
Try setting your second hdd as the boot media in your bios you should then get grub running which will allow you to select which os to boot

---

### Post by darolu on 2010-02-26
Yes, installing Windows will cause that, it rewrites the MBR, preventing GRUB to boot your computer. Read this links, you'll find everything you need to fix it there:

If you use GRUB2 (if you installed 9.10 "karmic"):
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

If you use GRUB (i.e. if you updated from 9.04):
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by mick222 on 2010-02-26
He should already have grub installed he installed Ubuntu after windows but on a different hdd so changing boot preferences should work.

---

### Post by scumboss on 2010-02-26
> **mick222 said:**
> Try setting your second hdd as the boot media in your bios you should then get grub running which will allow you to select which os to boot

Thanks that worked great.

---

