---
title: "Need some creative install ideas"
date: 2012-07-19
forum: General Help
---

### Post by Bartender on 2012-07-19
In the past I've read forum posts where people suggested that you could -
 
#1 Start installing Ubuntu to a HDD on one PC
#2 Shut down the PC and remove the drive at the point where the installer wants to restart the PC
#3 Take that drive to another PC, plug it in and start it up 

This was suggested as a way to get around a PC with a broken optical drive, no USB boot option, etc.  Does it work?  

I have an HP nc6000 notebook.  These old corporate notebooks came with a Multi-Bay docking mechanism.  You can remove the optical drive caddy and pop a HDD caddy in.  I have a SATA HDD caddy, and would like to boot from the caddy instead of the primary PATA HDD.

But if I pull the optical drive caddy out and plug in the SATA HDD caddy, I have no optical drive.  BIOS doesn't show any USB boot option.  So I'm kinda stuck unless I can do something like described above.

---

### Post by zero2xiii on 2012-07-19
Hay,

Most harware dont have an "option" for booting usb media.

Insert a usb stick (anything) and look if you have an option (usualy F11 of F12) to select the boot media and see if the usb media is listed as an option.

Also, have you concidered a network install if your bios supports that?

Further more, installing to a HDD and then plugging it into the new system and boot from it works very similar to a usb boot.

Also, you can (somewhat more advanced) set up grub on the spare drive and configure it to boot the ubuntu ISO from the drive, so you can do the full install onto the internal HDD.

Cherz and good luck :)

---

### Post by Bartender on 2012-07-20
I tried installing Xubuntu (known-good disc) to a SATA HDD in another laptop, then shut that laptop down without restarting and put the SATA HDD in the nc6000 caddy.  Set BIOS up to boot to the MultiBay first, then restarted it.  The HP nc6000's LED on the front edge of the chassis indicated that it looked at the MultiBay for several seconds, then moved on to the internal PATA HDD.

Dangit!

I bought the caddy on eBay.  It appeared to be unused.  I don't know if the problem is the caddy, the nc6000, or the way I installed Ubuntu onto the HDD before slotting it into the caddy.  When the HDD caddy is removed from the nc6000 and the DVD caddy is plugged in, the DVD works fine.

---

