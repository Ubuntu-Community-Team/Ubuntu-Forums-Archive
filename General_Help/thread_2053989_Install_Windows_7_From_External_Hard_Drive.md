---
title: "Install Windows 7 From External Hard Drive"
date: 2012-09-06
forum: General Help
---

### Post by SailboatOfDoom on 2012-09-06
Hi guys,

So I was looking into how to install Windows 7 from an external USB hard drive. I found a few different programs that allow you to do this by extracting the Windows 7 image file to the external hard drive in such a way that when you boot the computer up, it will boot from the external hard drive and bring you to the Windows 7 installation process. The only problem is they were Windows-only programs it seemed. I'm using Ubuntu 12.04 and was wondering how I could go about prepping my external hard drive the same way, but using an Ubuntu-friendly program.

Any help would be greatly appreciated, thanks guys!

---

### Post by Cheesemill on 2012-09-06
Does this help?
[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

I'm pretty sure that this will format your USB drive though, so make sure it doesn't have any important data on it before you run WinUSB.

---

### Post by sienile on 2012-09-06
The easiest way to do it would be to change your BIOS to boot the external HDD before the internal. If it's not hooked up it will default back to the internal.

---

### Post by HermanAB on 2012-09-06
Do yourself a favour and install Virtualbox and make a Windows VM and save it to a USB stick.  Then you never need to install Windows again.  When you need a fresh install, just copy the VM.

---

### Post by C.S.Cameron on 2012-09-06
To make W7 USB installer in Ubuntu, use gparted to format the USB drive NTFS and then set boot flag.
Use Archive Manager to extract the W7 iso to the USB.

---

### Post by C.S.Cameron on 2012-09-07
> **HermanAB said:**
> Do yourself a favour and install Virtualbox and make a Windows VM and save it to a USB stick.  Then you never need to install Windows again.  When you need a fresh install, just copy the VM.

I tried this booting Ubuntu from one flash drive and running XP.vdi located on another.
Autocad ran really slow.

---

