---
title: "How to tell if computer supports USB booting"
date: 2012-08-07
forum: General Help
---

### Post by Shadius on 2012-08-07
Hey everybody! :)

I'd like to know how to tell if a computer supports booting from the USB or not. 

Thank you.

---

### Post by efflandt on 2012-08-07
Go into CMOS setup from the BIOS splash screen with USB memory or drive attached and see if boot order or boot devices show the USB device as an option.  However, even if BIOS is set to boot USB before hard drive, you may still need to press whatever hotkey (typically F12 or Esc) in the BIOS splash screen to select the boot device (especially Dell computers).

My old laptop from 1/2000 definitely could not.  My old desktop at home and desktop at work from 2004 could boot from USB.  I seem to remember that a really low end laptop from 2005 could not, but most anything else newer than that should be able to boot from USB.

---

### Post by Shadius on 2012-08-07
Thank you for that reply. 

I have a friend who is trying to install Ubuntu via LiveUSB because the CD/DVD drive isn't working or something like that. Anyway, it gives a "Boot Error" message when he tries to boot from the USB. I've already given him instructions to change the boot order so that the USB is the first to boot, but still getting that error.

He also tried the same LiveUSB on a different computer, and it worked fine.

---

### Post by kurt18947 on 2012-08-08
I had the 'boot error' problem when using certain USB drives on one machine, a desktop with Gigabyte M.B./ modular BIOS.   The USB drive that shows 'boot error' on the Gigabyte M.B. would boot fine on an R61 Thinkpad.  What seemed to help was formatting in Windows, even doing a quick format.  I found this necessary even on USB drives with a factory format.  Lately I've been using Gparted, creating a FAT partition and make sure the boot flag is set.  I haven't seen 'boot error' in a while.

---

### Post by al-iksir on 2012-08-08
Hey, 

I'll simply attach my issue to this thread as it is related. 

I have a work-PC running with Win7 and wanted to try out booting Ubuntu 12.04 from a USB stick. However, does not work, Win7 keeps booting after restart as if I had changed nothing. 

Looked up the options in the BIOS, changed the boot sequence - nope. However, the options are a bit different from what I found in the support area here: USB-FDD, USB-ZIP and USB-CDROM but no USB-HDD or USB media. Does it mean my PC does not support booting from USB sticks?

Thanks,
al-iksir

---

### Post by kurt18947 on 2012-08-08
> **al-iksir said:**
> Hey, 

I'll simply attach my issue to this thread as it is related. 

I have a work-PC running with Win7 and wanted to try out booting Ubuntu 12.04 from a USB stick. However, does not work, Win7 keeps booting after restart as if I had changed nothing. 

Looked up the options in the BIOS, changed the boot sequence - nope. However, the options are a bit different from what I found in the support area here: USB-FDD, USB-ZIP and USB-CDROM but no USB-HDD or USB media. Does it mean my PC does not support booting from USB sticks?

Thanks,
al-iksir

I'm not 100% certain it's required but I have USB-HDD as my first boot device and it works pretty reliably.

---

