---
title: "Generic graphic drivers?"
date: 2010-02-14
forum: General Help
---

### Post by dmillerw on 2010-02-14
So I'm creating a minimal Ubuntu install for my thumb drive, and I'm not sure what computers I'll be using.

Is there any sort of generic video driver?

I'm asking because of I don't install drivers, its rather slow.

Any ideas?

---

### Post by Satoru-san on 2010-02-14
Yes, as a matter of fact your kernel comes with many different Graphic drivers.

If you are looking for one that will work on ANY card, use the "vesa" driver, this will be slow, so try to use the right driver for your hardware.

If you have an ATI card and are not worried about 3d, then you can use the xf86 driver, that I believe has support from the kernel but you still need to install it, I am not sure if it comes with the minimal install. apt-cache search ati will help you.

Same goes for nVidea cards.

---

### Post by 3rdalbum on 2010-02-14
If you don't have an /etc/X11/xorg.conf file, then Xorg will automatically detect what graphics card you have when you boot up, and use an appropriate built-in driver.

---

