---
title: "Ubuntu USB boot problem"
date: 2012-04-16
forum: General Help
---

### Post by JonathanUB on 2012-04-16
hi all,

I am trying to install Ubtunu 11.10, I have the iso on my usb stick etc and all formatted correctly with penlinux. I know it works because i've installed it on another computer.

On this laptop I have FreeBSD 9.0, and for some reason, when I boot from the USB,

it hangs on the "syslinux 4.06 etc etc" and I never get to the usual menu options with the
ubuntu logo etc.


Does anyone have an idea of what is wrong and how to fix this?


thanks in advance.

---

### Post by JonathanUB on 2012-04-17
bump - no one is familiar with this kind of problem?

---

### Post by oldfred on 2012-04-17
These are all older issues, so I did not think they apply, but you can check.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

