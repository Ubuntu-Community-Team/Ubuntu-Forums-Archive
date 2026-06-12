---
title: "USB 3.5&quot; Floppy Drive"
date: 2006-06-07
forum: General Help
---

### Post by fopetesl on 2006-06-07
Have a USB Mitsumi 3.5" floppy/stiffy drive.

The OS sees it but in a terminal reports:
[COLOR="Red"]**Partition x has different physical/logical beginnings (non-Linux?)**[/COLOR] Where 'x' is 1..4

Sure it's non-Linux, it's formatted as a FAT disc since I need to transfer data to & from a Windoze box.

I guess the OS is expecting a usb format device.

How do I persuade the OS to see a 'normal' floppy and respond accordingly?

---

### Post by fopetesl on 2006-06-07
OK. Have the first part sorted. Enter:
[COLOR="Blue"]/dev/sda    /media/usbfdd    auto   rw,noauto,user 0   0[/COLOR]
into [COLOR="DeepSkyBlue"]/etc/fstab[/COLOR]
Then, (as root):
```
mkdir /media/usbfdd
chmod 777 /media/usbfdd
```
 and I can read/write a disc.
Note: perform the above without a disc in the device!

2nd part. How to format?  Usually we can```
fdformat /dev/fd0H1440
``` but this format doesn't exist on my computer and probably wouldn't work on a USB device.
Any clues?

---

