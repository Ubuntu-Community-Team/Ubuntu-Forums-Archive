---
title: "Unable to drop to console 10.04"
date: 2010-05-03
forum: General Help
---

### Post by Apewall on 2010-05-03
After 10.04 upgrade I cannot drop to console, as well as the gnome UI takes overly long to load, letting me stare at my background for 10 seconds before arriving.

Let me start off by saying my machine would not even boot when using the nouveau driver. After successfully installing the normal nvidia driver I was then able to get to my desktop.

However.

I cannot view any of the console's that are not using X
(F1 F2 etc) None of these work, previously I received invalid input on the nouveau driver but now when i drop to console I am met with a black screen and no display until I return to the one using X.

I suspect it is using an impossible resolution with the consoles but I cannot figure out how to fix it. Previously I would assume vga= tag in grub would resolve this, but grub2 seems to ignore these for display resolution.

I am using a TV/monitor that is 1360x768 @ 60hz


tried using
GRUB_GFXPAYLOAD_LINUX=1360x768

as well but recieve a black screen at console

---

### Post by klemes on 2010-05-03
My guess would be to make sure that you completely uninstalled any trace of the nouveau driver that has been quite possibly left behind, and to also completely uninstall the glx-nvidia driver too and then attempt a fresh installation of your video card's drivers from scratch.
use the 'dpkg -l |grep nouveau'
and the 'dpkg -l |grep nvidia' to see the relevant packages currently installed in your system.:D

---

### Post by swalker23 on 2010-05-03
> **klemes said:**
> My guess would be to make sure that you completely uninstalled any trace of the nouveau driver that has been quite possibly left behind, and to also completely uninstall the glx-nvidia driver too and then attempt a fresh installation of your video card's drivers from scratch.
use the 'dpkg -l |grep nouveau'
and the 'dpkg -l |grep nvidia' to see the relevant packages currently installed in your system.:D

I have the same problem as the OP, and I tried it with the nouveau driver and the one from nvidia page.  I can't drop into console with either.  With the nvidia driver from their page you have to remove nouveau in order to install it.

---

### Post by tgalati4 on 2010-05-03
After purging the nouveau driver did you reconfigure?

sudo dpkg-reconfigure -phigh xserver-xorg

Logout or reboot.

---

