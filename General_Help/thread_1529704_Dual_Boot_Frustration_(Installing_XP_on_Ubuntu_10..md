---
title: "Dual Boot Frustration (Installing XP on Ubuntu 10.04)"
date: 2010-07-12
forum: General Help
---

### Post by Gigashady on 2010-07-12
Hello, I am very new to this operating system, so please bare with me.

First off, I do not get the instructions from this page:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

... it is well beyond my knowledge capacity.

And yes, I am planning to dual-boot because the games that I play cannot run in this operating system (Ubuntu 10.04 Lucid Lynx LTS).

Is there an easier, dumber way to install Windows XP after Ubuntu 10.04 has been installed, in order to dual-boot?

Thanks in advance!

---

### Post by bodhi.zazen on 2010-07-12
> **Gigashady said:**
> Is there an easier, dumber way to install Windows XP after Ubuntu 10.04 has been installed, in order to dual-boot?

Thanks in advance!

No, the Windows installation is not as user friendly. It is far easier for new users to install Windows first, Ubuntu second, and then most everything is automatic.

If you go the other way, Ubuntu first, go ahead and install Windows.

Then all you need to do is boot a live CD and restore grub (the Ubuntu boot loader).

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Personally I prefer Method 3 , chroot, it is a few "simple" commands, but works well.

---

