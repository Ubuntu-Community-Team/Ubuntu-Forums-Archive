---
title: "BIOS boot sequence"
date: 2009-08-18
forum: General Help
---

### Post by texas.chef94 on 2009-08-18
Downloading ISO now for an install on new machine, but the disk location will be a USB drive. So should BIOS Boot sequence be HD then removable or removable first. Plus do I install grub to MBR.
Thanks

---

### Post by fragos on 2009-08-18
Tell your BIOS setup to use the CD before the hard disk and you'll be set. Burn your ISO to a CD and reboot with it in the CD drive and you're on your way to install Ubuntu. You need not change the BIOS back as it only boots from the CD when there is a boot able CD in it.

---

### Post by approaching on 2009-08-18
if you are putting the iso on the usb drive (there are plenty of tools out there to do this for you, it isn't just copying the file over), then yes, the removable device should boot before the hard drive. if the usb device is a disk drive, same deal.

if you don't plan on dual booting or anything like that use all of the defaults that use the whole disk etc and you will be fine.

---

