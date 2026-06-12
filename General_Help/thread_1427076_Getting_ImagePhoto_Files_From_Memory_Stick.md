---
title: "Getting Image/Photo Files From Memory Stick"
date: 2010-03-11
forum: General Help
---

### Post by mavigozler on 2010-03-11
The struggle I am having to get photos from a memory stick has been considerable!

I can see the photos in the camera's (Sony Cybershot DSC-H1) play mode on the memory stick (SanDisk Memory Stick PRO 4.0 GB MagicGate, Prod No SDMSV-4096).

My computer (HP Pavilion dv9500t) has Microsoft Windows Vista Home Premium (32-bit) with a multi-card reader (Ricoh 5-in-1 card reader).  Plugging the card into the reader brings up a prompt asking the user if he wants to format the disk in Windows Explorer.  I believe the file system is RAW format.  Having lost the original USB camera cable, I find another 5-pin mini cable (used for a Canon camera, hoping there is compatibility between Sony and Canon) and it brings up a "Removable Disk" with drive letter in Windows:  clicking it tells the user to insert a disk.

Having gone nowhere with Windows, I then hope Linux can recover it.

On my external hard drive (Western Digital 1 TB) I have a bootable Ubuntu 9.04 partition installed.  Plugging in the camera's USB cable connector, I see an unmounted indicator to a 4.0GB storage device.  When I click it (to mount it), I get a "Cannot mount volume.  Unable to mount the volume" prompt with the detail:  "/dev/sdd1: can't read superblock"

The camera can read the images.  But no computer I have running Windows or Linux can see the file system!  Recovering the photos is CRITICAL!

Anyone have ideas?

---

### Post by PRC09 on 2010-03-11
For windows you can try the following link,its free and works well.I have not had the problems with not being able to mount the drives I have worked on but I think it will scan anything that your machine can see....Good Luck...

[http://dmitrybrant.com/diskdigger](http://dmitrybrant.com/diskdigger)

---

### Post by mavigozler on 2010-03-13
Thanks for this.  It recovered many photo files using the "dig deeper" option to look for JPEG file signatures, but about 7 or 8 of the 350-360 photos had defects (grayed out portions of the image).

I also tried another data recovery tool found [here]("http://www.cgsecurity.org/wiki/PhotoRec") and compared the recovery, and I think it found 2-3 more photos, all without defect.

---

### Post by PRC09 on 2010-03-13
Glad it worked for you.....

---

