---
title: "NEC computers"
date: 2010-06-20
forum: General Help
---

### Post by cuberts on 2010-06-20
So I am at a NEC computer right now, and I am in another country. I have brought a flashdrive with Ubuntu installed, and now I was trying to boot from it, but to me it appears that id does not support booting from a USB flash drive. I do not know how you would access what would be the boot menu on a Dell computer. So does anyone know how to boot Ubuntu from a flash drive on a NEC computer??

---

### Post by iponeverything on 2010-06-20
probably does not boot from usb. To be sure just put the model number into google along with a couple of other key words. If you don't see the option to boot from usb in the bios, odds are it can't do it.

---

### Post by ronnielsen1 on 2010-06-20
I believe UBCD will give you the option


[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)


[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

I couldn't find a newer usb boot from cd how to

> This ***USB Boot CD*** can be used to boot a [URL="http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#"][COLOR=#009900][COLOR=#009900 ! important][COLOR=#009900 ! important]Ubuntu[/COLOR][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL] 8.10USB flash  drive on computers with a BIOS that does not natively support booting  from USB. The boot CD contains a grub bootloader that loads the initrd  and vmlinuz kernel from the CD and then proceeds to locate the  filesystem on the USB flash drive. Because the USB [[COLOR=#009900][COLOR=#009900 ! important][COLOR=#009900 ! important]drivers[/COLOR][/COLOR][/COLOR]]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#") are preloaded from  the initrd on the CD, the USB flash drive can then easily be detected.

---

### Post by cuberts on 2010-06-22
So what are the types of computers that are capable of booting from a USB flashdrive??

---

### Post by 3rdalbum on 2010-06-22
> **cuberts said:**
> So what are the types of computers that are capable of booting from a USB flashdrive??

If it is made in the last few years, it should support USB booting, but you will need to set the USB device to boot in the computer's BIOS setup menu.

---

