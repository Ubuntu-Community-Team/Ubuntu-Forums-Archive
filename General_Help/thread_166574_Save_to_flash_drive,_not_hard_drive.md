---
title: "Save to flash drive, not hard drive"
date: 2006-04-26
forum: General Help
---

### Post by Martin P on 2006-04-26
How do I tell Ubuntu to save a document to the flash drive and not to the hard drive?

---

### Post by Ramses de Norre on 2006-04-26
Save as, choose other in the drop down box for the location and browse to the flash drive?

---

### Post by Martin P on 2006-04-28
Thank you for replying. I do not have a Location field. The only fields with drop down lists are File name: and File type:.

---

### Post by tburns on 2006-04-28
save as...

the usb needs to be inserted and mounted. You have to save to the mount point. cat /etc/fstab should give you the mount point for the usb, my usb is /dev/sda1.

or you can stick in the drive, let ubuntu automount the usb drive and popup the nautilus window. and you can save as..  or drag and drop into the window.

---

### Post by tburns on 2006-04-28
or if you like the command line...
man cp

cp /file/to/copy /file/that/is/the/copy
again /usb or other mount point is the target directory not /dev

---

