---
title: "boot error from USB installation"
date: 2010-10-04
forum: General Help
---

### Post by aloishis89 on 2010-10-04
I recently installed Ubuntu onto a USB drive and it was working perfectly. Today I tried booting from it like usual and it hung on the splash screen with the 4 little dots. I hit F8 to see what was going on and saw this:

[http://img39.imageshack.us/img39/7779/imag0056yp.jpg](http://img39.imageshack.us/img39/7779/imag0056yp.jpg)

I made sure that the drive had been removed safely from windows and that my hard drive had been correctly unmounted when windows shut down. I really need to get this working because it has some code on it that I was developing that I need to finish since it's due soon.

---

### Post by aloishis89 on 2010-10-05
I tried performing a disk check from gparted and now I get a new error when booting:

mountall: connection is closed

Any ideas? Alternatively, is there a way to recover files from the drive? If I could copy over a couple files that were on my desktop, I could just reformat and reinstall ubuntu on the thumb drive.

---

### Post by C.S.Cameron on 2010-10-05
You should be able to open the drive from another computer running Ubuntu.
If it is a persistent, (disk image), install, you can access the contents of casper-rw as shown on the page below:
[http://ubuntuforums.org/showthread.php?t=1246318&highlight=usb](http://ubuntuforums.org/showthread.php?t=1246318&highlight=usb)

---

