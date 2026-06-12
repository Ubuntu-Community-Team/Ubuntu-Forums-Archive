---
title: "ubuntu on a usb key?"
date: 2011-04-19
forum: General Help
---

### Post by asdfghjkl67 on 2011-04-19
First off how do i make a live cd boot up on a usb key? 

Secondly does a ubuntu usb key retain logs after you turn it off? 

Thirdly how do i know if my laptop supports booting from usb-would that be in the bios screen options?

---

### Post by C.S.Cameron on 2011-04-19
Try Startup Disk Creator from the Live CD, you can also extract usb-creator for Windows from the Ubuntu iso.
There is and option to Use Extra Space when running these installers, this makes the drive persistent, saves changes.
On a new computer set the USB flash drive as the first hard drive in BIOS.

Or you can install to USB just like to internal drive, Unplug the internal drive first though.

---

### Post by asdfghjkl67 on 2011-04-19
> **C.S.Cameron said:**
> Try Startup Disk Creator from the Live CD, you can also extract usb-creator for Windows from the Ubuntu iso.
There is and option to Use Extra Space when running these installers, this makes the drive persistent, saves changes.
On a new computer set the USB flash drive as the first hard drive in BIOS.

Or you can install to USB just like to internal drive, Unplug the internal drive first though.

If i were to operate the usb drive as the first drive in bios while connected via the usb port on the laptop would there be logs left of what i did during that session? or is a physical live cd the only way to prevent logs from being made locally on the laptop?

---

### Post by C.S.Cameron on 2011-04-19
It is not that easy to write to the internal drive booting from a pendrive, least wise accidentally.
You should be as safe as with a CD.
If you are using the persistent mode everything is saved to a file named casper-rw on the pendrive.

---

### Post by s3a on 2011-04-19
Look into unetbootin.

---

