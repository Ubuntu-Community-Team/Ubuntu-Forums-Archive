---
title: "Boot problem after install"
date: 2010-06-30
forum: General Help
---

### Post by Jabbap on 2010-06-30
Hi there. I've never used Ubuntu (or any Linux distribution), so bear with me, please!

I've installed Ubuntu on my ASUS N61Jv notebook. I have an i5 2.27GHz processor, 4GB DDR3 RAM, with Windows 7 64-bit Home Edition as my primary OS. The computer has a NVIDIA GeForce GT 325M video card, with 1GB VRAM. 

I run the installer off of USB stick, and everything goes fine. I boot up the OS for the first time, and it finishes the installation with no problems. However, when I reboot again after installing the driver for the graphics card and boot up Ubuntu, my laptop's screen doesn't turn on. Windows 7 boots normally if I reboot again, but the screen stays powered off when I boot into Ubuntu. I assume this has something to do with NVIDIA's Optimus technology... is there a workaround for that?

---

### Post by davidmohammed on 2010-06-30
welcome,
  suggest give the following a try, 
  on the screen that you choose to run ubuntu or windows (its called the grub screen) - press e.

On the line containing quiet splash add nomodeset before quiet splash

e.g.

... nomodeset quiet splash --

press CTRL + X to boot.

---

