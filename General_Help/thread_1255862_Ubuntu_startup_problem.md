---
title: "Ubuntu startup problem"
date: 2009-09-02
forum: General Help
---

### Post by drewciferPAIN on 2009-09-02
Hello I'm new to Ubuntu and lately I've been attempting to install Ubuntu on my flash drive and run it persistently. I followed the tutorial from [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) .  I can boot the first menu screen, and I hit "run persistently" and the loading screen pops up and it loads for a bit, but then it goes to a black screen and the error messages "[135.300960] end_request: I/0 error, dev fd0, sector 0" and "[more random numbers] Buffer I/0 error on device fd0, logical block 0" appear repeatedly. It hangs there with more and more of these messages appearing.  I run Vista with SP1.  In addition, I attempted to run from a boot cd, but that failed as well, except my computer just became unresponsive and the monitor received no signal after the Ubuntu load screen.  Please help!

---

### Post by P4man on 2009-09-02
Ive seen those "Buffer I/0 error on device fd0" messages booting from an usb stick. Its like its trying to read the floppy drive, and it takes forever to figure out there isnt one (or no floppy in it). But eventually it continues booting. Either wait longer, or disable the floppy in your bios.

As for the other error, that looks more serious. What sort of machine are you trying this on ?

---

### Post by drewciferPAIN on 2009-09-02
I'm running a custom built machine:
p5N-E SLI motherboard
Intel core 2 due E8400@3.00 GHz
nVidia GeForce 8800 GT
Hitachi HDT725032VLA SCSI hard drive
And like I said before, Vista w/ SP1.  I also don't have a floppy drive, but I'll see what's in the BIOS and I'll let it try to boot up while I go to class.

---

