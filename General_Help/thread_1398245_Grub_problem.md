---
title: "Grub problem"
date: 2010-02-04
forum: General Help
---

### Post by johnmar on 2010-02-04
I am using dell latitude D830 with bios revision A14.
I installed windows 7 from a usb some months ago.
Then using VirtualBox i installed ubuntu 9.10 in my usb stick.
I booted the computer through it and decided to format my hard drive
and install both windows and ubuntu.
I booted in windows (usb on the pc), erased the usb and backed up some of my files.
Then next morning i tried to boot the laptop and it gives a blank screen saying
 
GRUB loading.
error: no such disk
grub rescue>
 
i tried booting from usb (windows 7 installation disk) but it shows
the same screen. Is there any way to boot in windows???

---

### Post by audiomick on 2010-02-04
It looks like your grub is looking for something that was on whatever is was that you formatted.

I gather that you only have windows on the machine at the moment.
You will need to restore the mbr to boot windows.
Info here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
point 16 is what you need.

---

### Post by johnmar on 2010-02-04
thanks michael i m trying it now

---

### Post by CrusaderAD on 2010-02-04
Audiomick is right. You need to restore the Windows boot loader.

---

### Post by johnmar on 2010-02-04
It worked!!! Thanks for your help

---

