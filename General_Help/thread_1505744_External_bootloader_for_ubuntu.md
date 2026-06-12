---
title: "External bootloader for ubuntu?"
date: 2010-06-09
forum: General Help
---

### Post by 6sicSIX on 2010-06-09
hello, first post here.
Is it possible to install ubuntu 10.04 on a second partition without overwriting the windows7 bootloader and boot it using grub on a usb stick?

I would be happy with just the second option as I could fix mbr if I have to, I just don't want it to easily visible that linux is installed as well as windows :)

---

### Post by arrange on 2010-06-09
Should be possible (though I haven't tried it myself) provided that
 * the computer can boot from a USB device
 * you click on *Advanced* button in the final stage of installation and specify clearly where to put the Grub bootloader

(see step 8 in [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall))

---

### Post by stlsaint on 2010-06-09
> I just don't want it to easily visible that linux is installed as well as windows???

A statement for suspicion!

---

### Post by bodhi.zazen on 2010-06-09
> **6sicSIX said:**
> hello, first post here.
Is it possible to install ubuntu 10.04 on a second partition without overwriting the windows7 bootloader and boot it using grub on a usb stick?

I would be happy with just the second option as I could fix mbr if I have to, I just don't want it to easily visible that linux is installed as well as windows :)

You can install grub on the second hard drive.

Many BIOS give you the option of which hard drive to boot from during the boot process.

To boot windows , boot the first HD

To boot ubuntu, boot the second.

---

### Post by 6sicSIX on 2010-12-22
Why yes, hiding anything is generally suspicious lol.

Thanks for the replies. I went with the usb method in the end.
It is a single hdd laptop so I repartitioned the drive.

Peace out.

---

