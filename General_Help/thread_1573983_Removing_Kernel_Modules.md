---
title: "Removing Kernel Modules"
date: 2010-09-13
forum: General Help
---

### Post by oliverrichard47 on 2010-09-13
Hi, I recently added the eth1394 module to the kernel using the modprobe command.  Unfortunately the computer crashed almost instantly and now crashes on every boot.

Is there any way I can remove this module using a LiveCD?

Thanks, roliver

---

### Post by philinux on 2010-09-13
> **oliverrichard47 said:**
> Hi, I recently added the eth1394 module to the kernel using the modprobe command.  Unfortunately the computer crashed almost instantly and now crashes on every boot.

Is there any way I can remove this module using a LiveCD?

Thanks, roliver

It's the same command to remove it.
[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

Maybe from a chroot from the livecd. This guide shows how to set up a chroot as part of the tutorial.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by oliverrichard47 on 2010-09-13
> **philinux said:**
> It's the same command to remove it.
[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

Maybe from a chroot from the livecd. This guide shows how to set up a chroot as part of the tutorial.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Thanks for the speedy reply... I was also thinking of chroot but was unsure whether or not it would work in this circumstance as I've only ever used it a couple of times.

Thanks again, roliver

---

