---
title: "Problems booting my computer from USB for reinstallment of Maverick Meerkat..."
date: 2012-02-28
forum: General Help
---

### Post by Dr Heelhook on 2012-02-28
Hi, I have a computer on which I have installed Ubuntu Maverick Meerkat. For some reason, the operative system started working badly, so I decided to reinstall it on the computer. I still have the USB stick I used when I installed it in the first place, so I tried to boot the computer from the USB, but all that happens is that it says: 

"No DEFAULT or UI configuration directive found!"

What do I have to do to be able to boot from the USB and reinstall Meerkat?

---

### Post by oldfred on 2012-02-28
There were several issues, not sure which fix may work.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

