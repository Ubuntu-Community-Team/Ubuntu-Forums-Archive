---
title: "Quick &amp; easy usb persistent fix for 9.04"
date: 2009-08-22
forum: General Help
---

### Post by squashpup on 2009-08-22
Persistence, I believe, is broken in 9.04 when booting from a USB drive.  In other words, documents and settings are not saved from one boot to the next. After working with it all day, I found an easy fix...

If you haven't already, make USB drive using System>Administration>USB Startup Disk Creator.

When that finishes,

1) Open a terminal.  At the prompt, type:

dd if=/dev/zero of=casper-rw bs=1M count=1024
(replacing 1024 with the "size in MB" you wish to use for saving changes persistently)

2) Wait for this to finish.

3) At the prompt, type: 

mkfs.ext3 -F casper-rw

4) Insert pendrive.  Find "casper-rw".  Delete it and replace with the brand new "casper-rw" from your home directory.  Make sure you copy it to the top-level directory on your USB Startup Disk. 

5) Reboot to your USB Startup Disk.  Make changes and reboot to test.

6) Something else that I tried might help.  When I tell it to reboot or shut down, I let ALL of the time tick off when it says, "The computer will reboot/shut down in 60 seconds".  I think you have to give it time to write the info back to the disk.

---

### Post by Mighty_Joe on 2009-08-24
> **squashpup said:**
> Persistence, I believe, is broken in 9.04 when booting from a USB drive.  

For casper-rw file sizes above 2GB, yes. I linked to the [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") in the thread you just [linked to here]("http://ubuntuforums.org/showthread.php?t=1217620")

---

### Post by squashpup on 2009-08-24
Ahhh.  OK.  

So, if you stay under that size, everything is OK.  

Good to know, though, that you can fix it without starting the USB Key creator from the beginning.  This was pretty quick and easy.  

Thanks!

---

