---
title: "Startup Disk Creator created drive doesn't recognize space"
date: 2010-05-22
forum: General Help
---

### Post by DKuntz2 on 2010-05-22
I created a bootable usb drive using the startup disk creator, told it to store all of the drive in reserve, and installed.

I keep getting messages saying I don't have enough space, but the disk analyizer says I'm only using 1.6bg (seems large to me) and have 1.1 available.  Yet the section that shows me what's used where tells me that 100% of my 3.2gb is used.

I have no idea what's going on, can anyone help?

---

### Post by wilee-nilee on 2010-05-22
> **DKuntz2 said:**
> I created a bootable usb drive using the startup disk creator, told it to store all of the drive in reserve, and installed.

I keep getting messages saying I don't have enough space, but the disk analyizer says I'm only using 1.6bg (seems large to me) and have 1.1 available.  Yet the section that shows me what's used where tells me that 100% of my 3.2gb is used.

I have no idea what's going on, can anyone help?

Try sudo apt-get autoremove then sudo apt-get autoclean.
You probably have a cache with stuff in it. Also if you used a not up to date starting ISO and did updates this may be taking up the space. Also did you slide the adjust all the way to the right.

---

### Post by efflandt on 2010-05-22
Not sure what is giving you an error that you do not have enough space.  You are not trying to install updates on the USB iso are you?  You can install additional programs, but should avoid doing updates, because things in the original iso boot before your persistant partition (casper-rw file) is mounted.

If you used all available space for persistent data, then the FAT32 partition on your USB does not have any available space.  So maybe you are confusing available space within your persistent data (casper-rw file mounted as a loop device) and the FAT32 partition which with CD iso data and casper-rw file is full.

---

