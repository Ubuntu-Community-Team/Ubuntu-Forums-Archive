---
title: "ubuntu 11.04 installation problems"
date: 2011-06-14
forum: General Help
---

### Post by pr3zident on 2011-06-14
everytime i try to install ubuntu 11.04 the screen is just black is there any fix for this ?

---

### Post by mister_playboy on 2011-06-14
What medium are you trying to install from?  Do you have your BIOS set to allow booting from this device (USB drive, CD, etc)?

---

### Post by pr3zident on 2011-06-14
> **mister_playboy said:**
> What medium are you trying to install from?  Do you have your BIOS set to allow booting from this device (USB drive, CD, etc)?


im trying to install using usb drive and my cpu allows it

---

### Post by mister_playboy on 2011-06-14
I would suggest going into your BIOS (hold down a certain key when first turning on the computer, usually ESC or F2) and checking that booting from USB drive is enable and set higher in the boot order than the other options.

When I installed Xubuntu two days ago I wasted 30 minutes trying to figure out why my USB install wouldn't start... I had disabled "Allow External Boot Devices" after my last install.

Sorry I can't be more specific, each BIOS is different.

---

### Post by pr3zident on 2011-06-14
> **mister_playboy said:**
> I would suggest going into your BIOS (hold down a certain key when first turning on the computer, usually ESC or F2) and checking that booting from USB drive is enable and set higher in the boot order than the other options.

When I installed Xubuntu two days ago I wasted 30 minutes trying to figure out why my USB install wouldn't start... I had disabled "Allow External Boot Devices" after my last install.

Sorry I can't be more specific, each BIOS is different.

I understand what your saying it's just that i have done this process before but only when im trying to install 11.04 it installs but when starting up the screen just stays black and doesn't load up the user interface.

---

### Post by mister_playboy on 2011-06-14
If you don't have anything else plugged in the USB slots that might be intercepting the boot process, then I would try re-creating the USB boot image, perhaps it is flawed.  If your USB drive has an activity LED, does it flash while the screen is blank? (implying the installer is working but not visible).

If you've run Linux on that hardware before, then the chance that the installer is working correctly but can't even manage low resolution graphics seems extremely unlikely.

Sorry, I don't really have any other ideas.

---

### Post by mastablasta on 2011-06-14
try using alternate install image. it should be a text installer and then you can add proprietary graphics drivers (if necessary) before reboot.

---

