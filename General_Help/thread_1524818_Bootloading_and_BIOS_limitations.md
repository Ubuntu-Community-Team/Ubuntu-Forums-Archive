---
title: "Bootloading and BIOS limitations"
date: 2010-07-05
forum: General Help
---

### Post by Archeleus on 2010-07-05
As some of you may know, some BIOS' don't allow you to boot from an external device if the partition is at the back of the file system. I thought BIOS limitations were history but apparently it still exists. I don't think this can be fixed with a LILO/GRUB fix?
 
The linux partition on my external drive resides after around 270 GB, so when I boot, GRUB goes into rescue mode with "Unknown Filesystem" error. I already tried loading the images and setting root manually to boot, but grub rescue says that "boot" command is not found. I can't even go to the normal grub mode.
 
Should I update the bootloader/install LILO?
 
Also, if there is a way to bypass this restriction without moving the partition to the front of the disk, let me know. I don't really want to back up all that data. The drive is kind of full.
 
Cheers

---

