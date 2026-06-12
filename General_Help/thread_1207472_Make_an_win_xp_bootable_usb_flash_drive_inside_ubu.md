---
title: "Make an win xp bootable usb flash drive inside ubuntu"
date: 2009-07-08
forum: General Help
---

### Post by bigfas on 2009-07-08
I need to install XP on a usb flash drive cause for some reason my dvd drive stoped working.

I've seen a lot of guides but they all assumed that you have an working xp installation, I only have ubuntu installed. any help?

---

### Post by sedawk on 2009-07-08
Can you give more details please:

* What exactly do you need XP for (why is Ubuntu on USB not an option?)
* If your DVD drive is broken, how do you want to get the
  required XP files legally? Do you have them on disk already?

Talking about time and money: the cheapest solution is to
buy a new DVD drive, to get one from a friend (internal, or
external USB).

---

### Post by bigfas on 2009-07-08
> **sedawk said:**
> 
Can you give more details please:
* What exactly do you need XP for (why is Ubuntu on USB not an option?)


I need it to test software, websites, ecc

> **sedawk said:**
> 
* If your DVD drive is broken, how do you want to get the
  required XP files legally? Do you have them on disk already?


I have a legal Xp serial number, about the files I can download them from any torrent site.

---

### Post by Cheesemill on 2009-07-08
Are you trying to install XP **from** a USB drive or **onto** a USB drive?

---

### Post by bigfas on 2009-07-08
> **Cheesemill said:**
> Are you trying to install XP **from** a USB drive or **onto** a USB drive?

I'm trying to put the Xp files on a usb and then boot from usb as you will normally do with a cd, anyone ?

---

### Post by sedawk on 2009-07-16
Take some virtualization software like VirtualBox or free
VMWare server and install XP inside a virtual computer on
a (small) virtual harddisk.

If you need a portable USB stick with a rescue XP you might try to create
one from inside the virtual machine (Bart PE) or use the stick
itself as virtual disk. Otherwise use that virtual computer for testing.
Far better than messing around with the USB stick.

---

### Post by t4thfavor on 2009-07-16
> **sedawk said:**
> Take some virtualization software like VirtualBox or free
VMWare server and install XP inside a virtual computer on
a (small) virtual harddisk.

If you need a portable USB stick with a rescue XP you might try to create
one from inside the virtual machine (Bart PE) or use the stick
itself as virtual disk. Otherwise use that virtual computer for testing.
Far better than messing around with the USB stick.

Building on that approach, if you really need a bootable XP USB, you should be able to start an install from the CD, and then pick the USB disk as the install medium. make sure to unhook all your other HDD's so that the Windows boot-loader doesn't smite grub.

or 

install onto a real hdd, and then use DD to copy the image from the hdd to the USBDD. Both approaches should work just fine.

---

