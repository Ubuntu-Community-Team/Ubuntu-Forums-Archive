---
title: "Floppy disk emulation?"
date: 2011-02-24
forum: General Help
---

### Post by kahlil88 on 2011-02-24
Is there any way to emulate a floppy disk? I have one of those horrid BIOS updates that has to be written to a floppy disk. I don't have a floppy drive, nor do I wish to bother with one, so I need to trick it somehow into writing the boot disk data to an image file or directory or something. I've tried running it in Wine with a particular directory mapped to the A: device but I just get errors. Won't open in File Roller either.

---

### Post by Hippytaff on 2011-02-24
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1035940")

---

### Post by mastablasta on 2011-02-24
you can't emulate this kind of thing just as you can't change a tire while driving. :-)
 
try to put it on CD or USB key. It's likely a DOS boot disk.

---

### Post by Hippytaff on 2011-02-24
> **mastablasta said:**
> you can't emulate this kind of thing just as you can't change a tire while driving. :-)
 
try to put it on CD or USB key. It's likely a DOS boot disk.
 
My brain totally did not absorb the bios update bit :?

---

### Post by kahlil88 on 2011-02-24
> **mastablasta said:**
> you can't emulate this kind of thing just as you can't change a tire while driving. :-)
 
try to put it on CD or USB key. It's likely a DOS boot disk.

My idea is to put it on a USB key with FreeDOS like the last BIOS update I did. The problem is actually getting the BIOS ROM file, which is buried deep within the evilly encrypted executable that demands a floppy disk.

---

### Post by mastablasta on 2011-02-24
perhaps then you should contact motherboard or BIOS manufacturer and ask them WTF?! how to update with no floppy? :-)

---

### Post by psusi on 2011-02-24
You need to map the A: device to a 1440K image file, not a directory.

---

