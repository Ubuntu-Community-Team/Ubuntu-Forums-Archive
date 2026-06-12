---
title: "I can't boot from USB Flash Drives, even though I should be able to..."
date: 2009-12-21
forum: General Help
---

### Post by Psumi on 2009-12-21
My motherboard is a GIGABYTE motherboard... but, there are three USB Options:

USB-CDROM
USB-FDD
USB-HDD

None of these would boot to my 2 GB Flash drive after using unetbootin to make a bootable flash drive with windows. Does anyone know why it didn't boot to the flash drive?

Yes, I have Legacy USB Enabled (Have to, in order to use my keyboard in CLI Setup of mini.iso)

I used mini.iso ubuntu, fedora, and ubuntu, and none of them would boot with the flash drive. So instead, I just installed mini.iso from the CD-RW I have laying around, but now that I'm in linux, should I try the usb-startup-disk creator or whatever instead of unetbootin? If so, what package do I install to use that program? I installed gnome-core, so I don't have it.

---

### Post by Lukas666 on 2009-12-21
> **Psumi said:**
> My motherboard is a GIGABYTE motherboard... but, there are three USB Options:

USB-CDROM
USB-FDD
USB-HDD

None of these would boot to my 2 GB Flash drive after using unetbootin to make a bootable flash drive with windows. Does anyone know why it didn't boot to the flash drive?

Yes, I have Legacy USB Enabled (Have to, in order to use my keyboard in CLI Setup of mini.iso)

I used mini.iso ubuntu, fedora, and ubuntu, and none of them would boot with the flash drive. So instead, I just installed mini.iso from the CD-RW I have laying around, but now that I'm in linux, should I try the usb-startup-disk creator or whatever instead of unetbootin? If so, what package do I install to use that program? I installed gnome-core, so I don't have it.

What motherboard?

I have GA-p55m-ud2

and my MB treats USB flash drives as regular hard drives.  Go to BIOS and check the boot order in the HDD section (move your USB drive to top). In my case it was all about it.

Then boot as usually.

---

### Post by Psumi on 2009-12-22
Yeah, my motherboard does the same. Thank you.

But when I tried to boot into Fedora Live XFCE via my USB Drive, it gave this error: **Booting failed. Sleeping Forever**.

I can't use USB-Startup Creator either, it will either not load the ISO and take data from my CD Drive, or it will not format the USB Drive because it's not found.

---

### Post by Lukas666 on 2009-12-22
> **Psumi said:**
> Yeah, my motherboard does the same. Thank you.

But when I tried to boot into Fedora Live XFCE via my USB Drive, it gave this error: **Booting failed. Sleeping Forever**.

I can't use USB-Startup Creator either, it will either not load the ISO and take data from my CD Drive, or it will not format the USB Drive because it's not found.

I would check it on another computer first. And do you have access to Windows? I know good software for windows for creating bootable sticks.

---

### Post by Psumi on 2009-12-22
> **Lukas666 said:**
> I would check it on another computer first. And do you have access to Windows? I know good software for windows for creating bootable sticks.

No, I do not have access to windows. I wish USB Startup and Portable Linux would create Fedora USB Images -_-

---

### Post by spiderbatdad on 2009-12-22
The usb start up creator in karmic doesn't work for me either. It would not format the drive...so I did manually, then it told me there was no space. I booted up an 8.10 live cd, and the start up creator from that cd worked like a charm.

---

### Post by Psumi on 2009-12-22
> **spiderbatdad said:**
> The usb start up creator in karmic doesn't work for me either. It would not format the drive...so I did manually, then it told me there was no space. I booted up an 8.10 live cd, and the start up creator from that cd worked like a charm.

It won't create a Fedora USB Though, it needs casper.

---

### Post by spiderbatdad on 2009-12-22
I used this to make a bootable usb DSL (fedora based), if you don't have a working copy of fedora perhaps this will do for you? [http://www.damnsmalllinux.org/wiki/index.php/Install_to_USB_From_within_Linux](http://www.damnsmalllinux.org/wiki/index.php/Install_to_USB_From_within_Linux)

---

### Post by miniyak on 2009-12-22
I've been having the same issue, the only thing close to getting what i wanted, was when i installed 9.10 on an internal drive on my tc4400, then took the 2.5 sata out a and put it in an enclosure. In this way I was able to boot a persistent install on usb hard drive on my Panp5. (but not the tc4400 suspiciously)

I have a 16gb flash that i have tried unet and usb startup disc creator on and i was only successful with unet once using the 9.04 iso. Between failing 11 or so times with the both of them. 

as far as the startup disc creator goes, reinstall it. I had better luck after doing this (to no success.. but things went smoother). Also, format your usb drive with a different program, like gparted. (dont forget to unmount before formating)

I dont think the problem is your motherboard based on what ive been seeing, but i could be wrong.

---

