---
title: "Unbuntu USB Creator for windows"
date: 2010-10-07
forum: General Help
---

### Post by ValtoTiger on 2010-10-07
Hello again, trying to create a bootable windows usb but I can't find any program that actually works on ubuntu. (trying to dual boot my computer). I tried googling but no go, I also used the built in usb creator but it won't upload the vista iso file. So yea can anyone help me find a usb software that will work. Also I tried wine to load wintoflash but it won't detect my flashdrive and I don't know why :/

---

### Post by ValtoTiger on 2010-10-08
._. bump

---

### Post by C.S.Cameron on 2010-10-08
The only method that I have found to run Windows from a flash drive is at:

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

This works for XP, I have not tried it with Vista.

If you just want to boot a Windows 7 install from flash then format the flash drive NTFS with gparted and set the boot flag, then copy the Win 7 disk contents to it.

---

### Post by C.S.Cameron on 2010-10-08
An option is to install Vuppy, (an off shoot of Puppy Linux that comes with V-box), or else NimbleX.

Then you can run any Microsoft O/S on the pendrive.

Vuppy is 116 MB and NimbleX is 204 MB.

I have both as part of a MultiBoot flash drive and I keep a XP vdi on a second drive. the vdi is 4GB and has Autocad, Rhino 3D, Sketchup and Caesar II.

---

### Post by MichaelSammels on 2010-10-08
I have a suggestion:

perhaps you could install something such as Bochs, or VirtualBox, and inside this install Windows, using the ISO (which I assume you have). Once inside Windows download the Windows 7 USB Download Tool (if it's Windows 7).

---

