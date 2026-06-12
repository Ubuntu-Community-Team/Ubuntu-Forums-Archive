---
title: "How to get usb stick to mount with write privileges?"
date: 2010-03-25
forum: General Help
---

### Post by MikeB23930 on 2010-03-25
I recently upgraded to xubuntu 9.10.  I regularly use usb sticks to transfer files from one machine to another.  When I mount a usb stick, it mounts with owner root, group my user account, and group privileges xr.  I have tried to change the privleges with sudo g+w to no avail.  Can some one walk me through setting up xubuntu to mount usb sticks so that the mounting user will have write prvileges?

Thanks,

Mike

---

### Post by bobcollard on 2010-03-25
> **MikeB23930 said:**
> I recently upgraded to xubuntu 9.10.  I regularly use usb sticks to transfer files from one machine to another.  When I mount a usb stick, it mounts with owner root, group my user account, and group privileges xr.  I have tried to change the privleges with sudo g+w to no avail.  Can some one walk me through setting up xubuntu to mount usb sticks so that the mounting user will have write prvileges?

Thanks,

Mike
Under System Menu open USB Startup Disk Creator and format the disk.  Stop at that point and you should have a clean thumb disk with full permissions.  Or, you could just format it on one of your other computers.  Most thumb drives are formatted FAT 16 or 32.  That makes them readable and writeable in most systems.  I use an Mac to do my formatting, just my preference.

---

