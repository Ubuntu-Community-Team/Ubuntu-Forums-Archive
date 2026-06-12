---
title: "USB problems after upgrade to 12.04"
date: 2012-05-14
forum: General Help
---

### Post by cm8000000 on 2012-05-14
Hi all, I was hoping to get some help:
Since upgrading to 12.04, I can no longer delete/move files on external drives (cameras, usb keys, etc). I get an error message (Error deleting file: -1: Unspecified error) after which the window with the drive's contents immediately disappears. After this happens, the usb ports on my tower no longer detect anything plugged into them. I have to reboot to get the usb ports working again. Any ideas as to what the problem could be? My knowledge of ubuntu is extremely basic. Thanks!

---

### Post by matt_symes on 2012-05-14
Hi


> **cm8000000 said:**
> Hi all, I was hoping to get some help:
Since upgrading to 12.04, I can no longer delete/move files on external drives (cameras, usb keys, etc). I get an error message (Error deleting file: -1: Unspecified error) after which the window with the drive's contents immediately disappears. After this happens, the usb ports on my tower no longer detect anything plugged into them. I have to reboot to get the usb ports working again. Any ideas as to what the problem could be? My knowledge of ubuntu is extremely basic. Thanks!

I have no idea what could cause that problem, but i would look in the kernel message ring buffer to see what is going on. That error message as displayed is hopeless.


Does it happen if you mount from the command line and delete a file that way ? 


Is the problem is just in the GUI ?



Open up a terminal (with no USB devices plugged on) and type


```
tail -f /var/log/dmesg
```
Plug in a USB device and mount it. 


Try to delete a file. 


When it falls over post the output of the tail command above back here. That may highlight if the problem is with the GUI or not.


Kind regards

---

### Post by cm8000000 on 2012-05-14
Thanks! I know the command you recommended wasn't a fix, it was to help get the error log, but somehow after I typed it and tried to do the delete, it worked! So I'm not sure if something self corrected, but if the problem pops up again I'll follow your instructions to post the error log. Thanks again!

---

