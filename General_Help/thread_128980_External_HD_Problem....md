---
title: "External HD Problem..."
date: 2006-02-12
forum: General Help
---

### Post by unexpected on 2006-02-12
I have an external HD (FAT32 partition) that I swap between my Ubuntu Desktop and my Windows Laptop. For some reason, when I mount it on the desktop now, it only reports ~55 megabytes of free space; however, when i connect it to my laptop, Windows reports a true total of ~40 gigs free space.

I thought this just might be a reporting error, but Ubuntu won't let me write anything to the drive, as it says there there is not enough space. If a try to write a comparatively large file on Windows, it writes fine. No matter how many files I write on the windows machine, when I mount it on Ubuntu, it still shows 55 megabytes free. Even if I delete files from this HD, it doesn't add the space, it still gives only 55 megabytes.

Does anyone know what's going on?

---

### Post by joft on 2006-02-14
Sounds like a typicall filesystem error/inconsistancy. Do you try to use "chdsk" under windows with it?

---

### Post by learning curve on 2006-02-14
Try converting your external drive to the NTFS file system.  I have had no problems with mine when switching back and forth from windows to Ubuntu.:cool:

---

