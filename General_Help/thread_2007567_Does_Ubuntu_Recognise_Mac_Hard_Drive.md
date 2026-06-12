---
title: "Does Ubuntu Recognise Mac Hard Drive?"
date: 2012-06-20
forum: General Help
---

### Post by arindamliveguitar on 2012-06-20
Hello.. i wanted to know that whether Ubuntu 11.10 recognises Mac Hard Drives or not? In case it doesn't, is there any software like Macdrive used in windows to accomplish a similar task in ubuntu? thanks a lot

---

### Post by manfromthezoo on 2012-06-21
Mac OSX filesystems are, these days, HPFS+ (unless someone's formatted the volume with a different filesystem - HPFS+ is the default and you'd have to go out of your way to change that).

I seem to remember plugging a HPFS+ formatted external drive to Ubuntu once, and had no problems reading from it.

Writing to it may be another issue - but I think even that is possible if you switch off the journalling from Disk Utility. That might cause some issues though if you're always moving the drive between your Ubuntu system and OSX.

If that's the case, you may want to use a more harmonious filesystem so the two OSs can both share the disk without any disasters.

---

### Post by 3Miro on 2012-06-21
Linux should open HPFS+ automatically, if not, open terminal and type:

```
sudo modprobe hfsplus
```
This will load the kernel driver for HPFS+.

---

