---
title: "URGENT: blacklist.conf accidentally deleted and original version needed!"
date: 2011-06-06
forum: General Help
---

### Post by srothe on 2011-06-06
Hi Forum,

I am very sorry to stir up dust with my first post, but pleeeease help me.

I am running Ubuntu 11.04 64-bit on a laptop. By accidant I deleted my /etc/modprobe.d/blacklist.conf file and now I do not know how to restore it. I used "rm" for deletion and meanwhile rebooted the machine. 

Unfortunately I am on a survey ship right now and we are about to leave harbour in 1 hour, which means we will be without internet in about 2 hours. 

Would it be possible for somebody, to post me an original blacklist.conf for this system? Or to send me a file via PM? Your help is really appreciated! All other ideas are very welcome...

thank you very much,

Stefan

P.S: Ideally it would be a blacklist.conf file in German language, as this is the system's default language.

---

### Post by dFlyer on 2011-06-06
unless you used sudo rm I don't see how you could have removed it. here is a copy from my 32 bit system.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by srothe on 2011-06-06
Thank you, Gary! :popcorn:

In fact I *did* use "sudo rm" :(. And yes, I will write 100 times "I shall not edit system files without creating a backup" :roll:

Stefan

---

