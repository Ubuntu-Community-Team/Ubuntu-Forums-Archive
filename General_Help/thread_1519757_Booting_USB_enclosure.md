---
title: "Booting USB enclosure"
date: 2010-06-28
forum: General Help
---

### Post by marshmallow1304 on 2010-06-28
I just installed Lucid on a 20 GB hard drive in a USB enclosure so I can use Ubuntu without disturbing the Debian install on the internal hard drive.  I unplugged the internal drive while installing.  The problem is that the BIOS does not detect the enclosure so I need a way to chainload grub.  I've tried PLoP Boot Manager (light on USB drive shuts off and nothing happens), SuperGrub (OS on USB drive not detected, even after enabling USB support), and grub legacy on the internal hard drive (USB drive not seen while using tab completion on
```
root (
```
).

Is there something I need to do to make grub mount the USB drive?  Is there another bootloader that can do this?

---

### Post by C.S.Cameron on 2010-06-28
If you unplugged the internal hard drive while installing to the external one then grub should have been properly installed to the external drive.
Is your bios set up to boot the external hard drive first?

---

### Post by marshmallow1304 on 2010-06-28
Thanks for the reply.  The BIOS doesn't detect the external drive at all.  Regular USB flash drives are recognized, but not this drive in an enclosure.  However, this is no longer a big concern because I found an internal hard drive that will work just fine for my purposes.

---

