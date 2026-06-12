---
title: "Trying to save a SD Memory card"
date: 2010-03-17
forum: General Help
---

### Post by arashiko28 on 2010-03-17
I have a 4GB SD memory card that was pulled out while still working on a windows machine and now I can't get it to work. I has a "superblock" and the partition name changed to mmcblk01 ie: dev/mmcblck01

From running fsck I get:

> fsck.vfat /dev/mmcblk0
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Logical sector size (35836 bytes) is not a multiple of the physical sector size.


I tried formatting but even though it says to be successful, I can't use it, it remains, empty.

---

### Post by llamabr on 2010-03-17
What happens often is that if you don't properly unmount it from windows, it will corrupt the filesystem, and then next time you plug it in, you'll get that error.  In windows,  you right click the little thing on the lower right to tell it to safely eject removable devices, or something.

You say you tried to format it.  What, exactly, did you do?

---

### Post by arashiko28 on 2010-03-18
I tried with gparted, it says it has been succesfully formatted, and it's clean, but the path name changed from sdb1 to mmckbl0. Now I can paste things to the memory while on the PC, but the camera can't store any picture.

*Is good to know I don't have windows on my computer, I borrowed the thing to a friend for a couple of minutes and then got it back like this.

---

### Post by joeknoodle on 2010-03-18
> **arashiko28 said:**
> I tried with gparted, it says it has been succesfully formatted, and it's clean, but the path name changed from sdb1 to mmckbl0. Now I can paste things to the memory while on the PC, but the camera can't store any picture.

*Is good to know I don't have windows on my computer, I borrowed the thing to a friend for a couple of minutes and then got it back like this.

You might be able to use the camera to reformat the card (backing up data first). If this doesn't work, maybe use that windows machine for a reformat, back to camera to reformat.

In my experience if I'm using a card almost exclusively for like a camera, then I prefer to use the format from the camera. It just seems to work with a bit less hassle that way. The camera will place what files it needs on the card, and these may not be available with the OS of other systems. I'm thinking that "sdb1 to mmckbl0" change is giving the camera grief.

---

### Post by audiomick on 2010-03-18
> **joeknoodle said:**
> You might be able to use the camera to reformat the card (backing up data first). If this doesn't work, maybe use that windows machine for a reformat, back to camera to reformat.

In my experience if I'm using a card almost exclusively for like a camera, then I prefer to use the format from the camera. It just seems to work with a bit less hassle that way. The camera will place what files it needs on the card, and these may not be available with the OS of other systems. I'm thinking that "sdb1 to mmckbl0" change is giving the camera grief.
I also think this is worth a try .

---

### Post by egalvan on 2010-03-18
> **arashiko28 said:**
> I tried with gparted, it says it has been succesfully formatted, and it's clean, 
. Now I can paste things to the memory while on the PC, 
**but the camera can't store any picture.**



As others have noted, you should reformat the card using the camera itself...

---

### Post by arashiko28 on 2010-03-21
> **egalvan said:**
> As others have noted, you should reformat the card using the camera itself...

I tried that even before posting the thread. No good. I'm giving up, nothing seems to work.

---

### Post by arashiko28 on 2010-03-23
THis got to a dead end, I'm marking it as solved and buy a new memory card. Thanks to all of you.

---

