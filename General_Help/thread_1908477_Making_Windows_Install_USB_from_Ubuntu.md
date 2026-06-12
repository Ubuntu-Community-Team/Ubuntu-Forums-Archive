---
title: "Making Windows Install USB from Ubuntu"
date: 2012-01-13
forum: General Help
---

### Post by memoryproblems on 2012-01-13
I am presently attempting to (re)install windows on netbook (no optical drive) using a USB flash drive from an .iso

I've done some searching and there are some tools out there to do it, but they are all made for Windows and I've had next to no luck attempting to run them through wine, and the only computer I have available to do this currently is running Ubuntu 11.10.

I did a search and found a post addressing this issue, however the solution was a youtube video link to a video that no longer exists :(

If anybody has any tips/advice on how to accomplish this, I would be greatly appreciative.

---

### Post by coldraven on 2012-01-13
I have never tried this but it might be what you're after.
[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by bluexrider on 2012-01-13
May try this

[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Good luck

---

### Post by C.S.Cameron on 2012-01-14
Using gparted format flash drive NTFS, set boot flag.
Copy contents of Win7 DVD to flash drive or extract iso to it using archive manager.
Set flash drive as first HDD in BIOS.
Done.

---

### Post by C.S.Cameron on 2012-01-14
Oops

---

### Post by ottosykora on 2012-01-14
> **C.S.Cameron said:**
> Using gparted format flash drive NTFS, set boot flag.
Copy contents of Win7 DVD to flash drive or extract iso to it using archive manager.
Set flash drive as first HDD in BIOS.
Done.


hmmm, but where is your step how to set up the boot file in the flash?

Those steps you mentioned do not work definitely, as you did not create any boot loader in the flash.

---

### Post by C.S.Cameron on 2012-01-14
> **ottosykora said:**
> hmmm, but where is your step how to set up the boot file in the flash?

Those steps you mentioned do not work definitely, as you did not create any boot loader in the flash.

Simply setting the boot flag in gparted has worked for me and many others.
Give it a try.

---

