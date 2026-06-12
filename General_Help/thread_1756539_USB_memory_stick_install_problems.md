---
title: "USB memory stick install problems"
date: 2011-05-12
forum: General Help
---

### Post by Robbyx on 2011-05-12
My usb stick will not allow me to easily copy and paste files on to it, or delete them once I no longer want them on the drive. Its owner is root. **How can I change the owner?** At the moment it is loading as a stylesheet in media/usb0. 

The file is transferring at a very low speed. 74mb  in 4 minutes

I suspect I will do better if I set up the drive via fstab. **What entry should I put in fstab for a USB stick drive?**

---

### Post by ManualSparrow on 2011-05-12
I don't the root ownership should affect the transfer, but [http://ubuntuforums.org/showthread.php?t=402813](http://ubuntuforums.org/showthread.php?t=402813) will probably help with the other problems.

---

### Post by coffeecat on 2011-05-30
@Robbyx, I've only just come across this thread, but I believe I have an answer.

> **Robbyx said:**
> My usb stick will not allow me to easily copy and paste files on to it, or delete them once I no longer want them on the drive. Its owner is root. **How can I change the owner?** At the moment it is loading as a stylesheet in media/usb0. 

The mountpoint /media/usb0 suggests you have installed the app usbmount. If you have, uninstall it. It is not designed for desktop systems and interferes with the USB automounting functionality built into the Ubuntu desktop.

---

### Post by Robbyx on 2011-05-30
I resolved the problem:

[LIST]
[*]Do not have a mount  command in fstab for the usb stick
[*]Remove UsbMount. Not suitable for non servers.
[/LIST]

---

