---
title: "USB drive owner seen as root, and I can't write to it"
date: 2011-05-29
forum: General Help
---

### Post by murphyac on 2011-05-29
When I installed Ubuntu, I was asked to enter a user name and password.  I chose one that would be a sort of "administrator alias" and gave it a strong password.  This is my "su" name and password.  That works fine for most things, such as installing software, etc..  Every so often, however, something comes up that can only be accessed by "root" and that is not me, even logged in with my "administrator alias" and password.  This happened when I inserted a USB flash drive and tried to copy some files to it that I wished to transfer from my desktop my laptop.  The only way I could do this was to format the flash drive. and then add my files to it.
      This morning I inserted the flash drive and tried to add another file to it, using "copy" and "paste".  Again I got "permission denied" and the owner of the flash drive, seen as "usb0", was again "root", and I could not change its permissions, because I am not "root".  It also says the device is not listed in etc/fstab.
      I have read the Ubuntu paper on mounting USB drives, but I'm not sure  that applies here.  The drive seems to be mounted, but with the wrong owner.
      This problem has also occurred with some software when I tried installing it.  I usually give up and don't install it.  This flash drive problem, however, is driving me crazy.  I need to transfer those files.  Is there something I'm missing?   Despite installing and upgrading Ubuntu on 2 machines, I'm still pretty much a newbie, and if it involves using the terminal, I need step-by-step instructions,
      I would be extremely grateful for any help forum members can give me.
Angela C. Murphy

---

### Post by coffeecat on 2011-05-29
It sounds as though you have installed the package "usbmount". If I'm right, I'll tell you how I knew. :) Uninstall it - it's not intended for GUI desktop environments. In fact it interferes with the inbuilt automounting function of Ubuntu. If you do that you will find that your USB drive will automount when you attach it and you will not need root privileges to use it.

---

### Post by murphyac on 2011-05-29
Thank you, thank you, thank you!
I did indeed have "usbmount" installed (when did I do that?).  I removed it and now I can read and write to the flash drive without any trouble.
Thank you again.
Angela C. Murphy

---

### Post by coffeecat on 2011-05-29
I'm glad it's fixed. A lot of people are getting caught by usbmount. 

Good luck!

---

