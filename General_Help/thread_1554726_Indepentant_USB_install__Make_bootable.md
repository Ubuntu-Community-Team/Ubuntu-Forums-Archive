---
title: "Indepentant USB install / Make bootable"
date: 2010-08-17
forum: General Help
---

### Post by Anleck on 2010-08-17
Hello, Ubuntu n00b here.

I have installed Lucid Lynx to a Usb stick - in doing so Vista boot loader was overwritten and I could not boot without the Usb stick.  I have reinstalled Vista so that I can access it like normal.  Now I cannot boot to the usb.  Is there a way I can add grub to the usb without overwriting the Vista bootloader again. I would like to have Ubuntu and Vista independent of each other.  I don't mind redoing the usb Ubuntu install.

Sorry if this is answered elsewhere but my net is capped at the moment - and is painful to hunt around for an answer.

Any help/advice would be appreciated.

---

### Post by Herman on 2010-08-17
You need to set the device to install GRUB to as the USB disk's MBR and not the internal IDE or SATA drive.
You can select it in step 7 of 7 of the installation by pressing the 'advanced' button.

---

### Post by Anleck on 2010-08-17
Thank-you Herman,

Being new to Ubuntu I stayed away from the advanced settings.  Will re-install and follow your instruction.  Looking forward to becoming more familiar with this operating system.

Thx for your time.  :D

---

### Post by Anleck on 2010-08-19
Success!

Finally got time to reinstall Ubuntu to the Usb - followed the instruction given about choosing where to place bootloader at step 7 - now everything is as I wanted it.

Thanks again Herman.

---

