---
title: "Running Ubuntu 10.04 in ram?"
date: 2010-09-28
forum: General Help
---

### Post by schwabdale on 2010-09-28
I can do this with Parted magic. Does anyone know how to Install and Run Ubuntu through ram only. No hard disk?

---

### Post by searchfgold6789 on 2010-09-28
Yup. Open up Gparted, right click your swap partition, and click swapoff to run ubuntu. I don't think it is possible to install it without making a swap partition.
You can also make a startup command ```
swapoff -a
```
to turn off the swap whenever you start Ubuntu.

---

### Post by schwabdale on 2010-09-28
Thanks for the post. But, I want to be able to run it off ram without the hard drive in the computer, or the cd in the computer.

---

### Post by KegHead on 2010-09-28
Hi!

I think the only way to do this is with damn small linux.

KegHead

---

### Post by MindCalamity on 2010-09-28
> **searchfgold6789 said:**
> Yup. Open up Gparted, right click your swap partition, and click swapoff to run ubuntu. I don't think it is possible to install it without making a swap partition.
You can also make a startup command ```
swapoff -a
```to turn off the swap whenever you start Ubuntu.

I think he wants to load Ubuntu to the RAM and start it from there, without installing to the hard drive at all... though I don't know if it's possible.

---

### Post by Altimos on 2010-09-28
RAM is referred to as "volatile" memory meaning it doesnt save anything in the chip like a hard drive does. as soon as you turn the power off, everything in the RAM is gone. you would need some type of data medium to save you OS to such as a CD, HDD, or USB flash drive.

---

### Post by schwabdale on 2010-09-28
> **MindCalamity said:**
> I think he wants to load Ubuntu to the RAM and start it from there, without installing to the hard drive at all... though I don't know if it's possible.

Correct! You can load Parted Magic to the ram and remove the cd and its very fast. 
I want to do this with Ubuntu

---

### Post by C.S.Cameron on 2010-09-28
Making Ubuntu Insanely Fast using RAM - Ubuntu Forums

[http://ubuntuforums.org/showthread.php?t=1499338&highlight=usb](http://ubuntuforums.org/showthread.php?t=1499338&highlight=usb)

---

### Post by schwabdale on 2010-09-28
I wonder what the boot time is?

---

