---
title: "error while copying from hard drive to usb stick"
date: 2010-07-11
forum: General Help
---

### Post by bokombrady on 2010-07-11
Hello
Got a problem. when I am trying to copy any of my files to usb stick, it gives me this alert: the folder cannot be copied because you do not have permissions to create it in the destination.
Do anybody have clue how i can resolve this? Many thanks.

---

### Post by dabl on 2010-07-11
Did you format the USB stick from Linux?  It is FAT16 or FAT32 format?

---

### Post by Dn4mycrownj on 2010-07-11
you have to remove usbmount in synaptice package manager and reboot and then run
run this in terminal 
sudo modprobe -r floppy

then reboot 
you will then be able to read and write to the flash drive.

worked for me on 10.04  i just go to places then computer  and the 4 i use all come up when inserted into the usb port. 

ref  [http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html)

---

