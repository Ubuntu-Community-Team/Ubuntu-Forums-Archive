---
title: "won't boot without using boot menu"
date: 2009-07-27
forum: General Help
---

### Post by ncumming on 2009-07-27
After doing a fresh install of 9.04 along side windows xp, I seem to be having a problem getting Grub to load.  When I boot my computer, after the "dell" screen, if I do nothing I get a blank screen with a flashing cursor.  In order to get GRUB to load, I have to hit F12 to bring up the boot menu, and then select "boot from SATA hard drive."  Then Grub comes up as normal.

In my bios, my boot order is boot from USB device, boot from CDROM, then boot from internal hard drive.  But neither my CDROM drive or USB has anything "bootable" in it, so it should go straight to the hard drive.  I don't understand why i now have to go to the extra step.

---

### Post by philcamlin on 2009-07-27
if you have any usb's plugged in unplug them 

i had that issue too

---

### Post by ncumming on 2009-07-28
That was it.  Never was a problem before, but for some reason an external hard drive i had connected must have been tripping it up.  I removed the usb drive from the boot sequence and everything works fine.

---

