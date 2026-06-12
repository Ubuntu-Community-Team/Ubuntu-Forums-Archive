---
title: "Install from USB flash drive"
date: 2011-05-22
forum: General Help
---

### Post by ladlers on 2011-05-22
My cd-rom is weak on my laptop and the laptop cannot boot from a usb flash drive. Is there any way to copy the installation iso file to a flash drive to INSTALL from there? I wouldn't trust gparted to run from a cd either.:guitar:

---

### Post by linuxinstalledfromhdd on 2011-05-22
The best thing to do in a situation like that would be to attempt a LAN network installation of Ubuntu.

---

### Post by ladlers on 2011-05-28
Thanks. I'm going to try wubi.

---

### Post by linuxinstalledfromhdd on 2011-05-28
Unetbootin is pretty good on windows to create a live usb stick of Ubuntu 10.10

[http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems](http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems)

---

### Post by nzjethro on 2011-05-28
I used unetbootin, and it worked fine for me! Much faster than a cd-ROM.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ladlers on 2011-05-29
The laptop DOESN'T BOOT from a usb stick.

---

### Post by MoebusNet on 2011-05-29
> **ladlers said:**
> My cd-rom is weak on my laptop and the laptop cannot boot from a usb flash drive. Is there any way to copy the installation iso file to a flash drive to INSTALL from there? I wouldn't trust gparted to run from a cd either.:guitar:

I think Smart Boot Manager may be an answer for you, if you can boot from a floppy:

[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

If not, maybe some of the other community documentation can give you some ideas.

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **ladlers said:**
> The laptop DOESN'T BOOT from a usb stick.

Have you researched if there is a BIOS update for your computer to enable the option?

---

### Post by MoebusNet on 2011-05-29
> **linuxinstalledfromhdd said:**
> Have you researched if there is a BIOS update for your computer to enable the option?

I second the suggestion; my Dell D800 wouldn't boot from USB until I updated my BIOS. Now it does! :)

---

### Post by ladlers on 2011-06-01
I know there is one remaining BIOS update but it doesn't mention booting from usb in the specs. I tried 10.04 via wubi and the logic isn't there to allow for wireless WEP encryption on my laptop, so I'll leave well enough alone. It does work stabily otherwise. I couldn't get the encryption to work on either 10.10 nor 11.04 on the boot cd.

---

### Post by sbraz on 2011-06-01
> **MoebusNet said:**
> I think Smart Boot Manager may be an answer for you, if you can boot from a floppy:

[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

If not, maybe some of the other community documentation can give you some ideas.

i've never tried it: i will.

anyway there's plop too:

[http://ubuntuforums.org/showpost.php?p=10890391&postcount=11](http://ubuntuforums.org/showpost.php?p=10890391&postcount=11)

[SIZE="3"][COLOR="Blue"]@ladlers[/COLOR][/SIZE]
check that thread too,

---

