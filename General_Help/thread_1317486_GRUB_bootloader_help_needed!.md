---
title: "GRUB bootloader help needed!"
date: 2009-11-06
forum: General Help
---

### Post by Cityscape on 2009-11-06
Hey,

I've had a Windows 98 and Windows 2000 dual-boot and now I'm installing Ubuntu 9.04 to complete my tri-boot. I'm using the Alternate install CD and my setup was almost done and now I get this message:
> The following other operating systems have been detected on this computer: Windows NT/2000/XP (loader)
If all of your operating systems are listed above, then it should be safe to install the boot loader to the master boot record of your first hard drive...Install GRUB bootloader to the master boot record?

What should I do? It is not showing my Windows 98 but only 2000. I don't want to lose access to either my 98 or 2000. Also my first HDD contains 98 and 2000, and I'm installing Ubuntu to my second hard drive.

Please help!

---

### Post by jollysnowman on 2009-11-06
I believe you can add it to /boot/grub/menu.lst

---

### Post by louieb on 2009-11-06
Because of the way MS sets up dual boot Grub will only be able to boot the one with the Windows boot loader. 

You should be ok to install to the MBR - after you select windows from GRUB your current boot menu will come up and you choose your flavor of Windows from there. 

tech stuff: [Multibooters, Pictures here worth 1000 words]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by Cityscape on 2009-11-06
Thank you for your help louieb. I chose to install it to the MBR and Ill let you know if it works when I complete the installation. :)

---

