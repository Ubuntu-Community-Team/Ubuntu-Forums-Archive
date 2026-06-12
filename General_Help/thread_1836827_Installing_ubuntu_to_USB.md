---
title: "Installing ubuntu to USB"
date: 2011-08-31
forum: General Help
---

### Post by cheat117 on 2011-08-31
Hi there guys!

I've tinkered with ubuntu to know that i can install the Live CD of ubuntu onto a disk but i want to install ubuntu itself on the usb. I know there's persistance, but thats not what im looking for, i have a 16gb flashdrive that i want to make as a rescue disk so to say.

I've looked all through google and couldnt find anything short of making it a persistent live cd.

help?

---

### Post by snowpine on 2011-08-31
It's just the same as installing to a regular hard drive. Use the regular Ubuntu installer and follow the normal procedure.

There is one "gotcha!" however and that is the GRUB bootloader. You must be careful to specify that GRUB is installed to the USB drive, not your internal hard drive. The easiest way around this is to physically disconnect your hard drive so the USB is the only drive attached. This way the installer will treat the USB as the first drive (/dev/sda) and install GRUB correctly.

---

### Post by cheat117 on 2011-08-31
all right i'll give it a shot!

---

### Post by snowpine on 2011-08-31
Good luck! I actually have an old, spare laptop with a busted hard drive that I use for testing Live CDs and making USBs. :)

---

### Post by jockyburns on 2011-08-31
I installed ubuntu 11.04 on my computer from a usb stick. Just google ubuntu  (should show the home page for it in search results), then just follow the instructions to download to a usb stick. I did it on my G/F's computer  (fatal HDD failure on mine so bought an new HDD) After reading up on the Ubuntu website, I realised I could boot directly from a usb stick. As I remember,(had a drink since then)  you have to download the usb installer first then download ubuntu to the usb stick. Simples (and so rewarding, I almost feel like a computer expert:lolflag: now )

---

### Post by jfed on 2011-08-31
Do you mean you want to install the OS on it, and boot from it, and use it? Or "burn" the .iso to it, so you can boot from it then install?

To do the latter, download a package called unetbootin

```
sudo apt-get install unetbootin
```

the program is fairly self explanitory

---

### Post by cheat117 on 2011-08-31
JFed: No i wanted the OS on the USB. Not the LiveCD

---

### Post by jockyburns on 2011-09-01
> **cheat117 said:**
> JFed: No i wanted the OS on the USB. Not the LiveCD

Do as I did in the post above., you'd have to enter the bios of your computer and set boot priorities to usb as first boot device (if there's already another OS on your HDD) When you use the usb stick to run ubuntu from, it does give you the option to install it, but if you only want to run from usb, then just don't ever install it. Shame if you then lose the usb stick though. :wink::wink::wink:

---

### Post by cheat117 on 2011-09-01
Jockyburns: thats persistance. I wanted it as though its a whole system on the flash drive

---

