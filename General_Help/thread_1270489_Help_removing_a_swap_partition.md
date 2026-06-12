---
title: "Help removing a swap partition"
date: 2009-09-19
forum: General Help
---

### Post by darlinsk on 2009-09-19
I have about 170 GB of disk space that I can't access because I have reached my maximum primary parition limit.  I'll spare you the details of how I came to be in this pickle, but hope someone can help me get out of it.  Here's my current configuration:

- HP Media Center with two 300 GB Drives, 3 GB RAM
- Dual Boot, (Vista & Ubuntu Hardy 8.04)
- BootIT NG to manage my boot menu and partitions
- Two 1.5 GB Swap partitions, one on each drive

All of the Ubuntu system is on a single drive, with the exception of one of the swap partitions.  I'd like to remove the swap partition on the 2nd drive, as this would enable me to increase the size of my extended partition, and gain access to the captive disk space.  

I've scoured this and other forums, but still can't figure out how to do it.  I tried clicking Swapoff, then deleting the partition -- which resulted in Ubuntu booting with a funky verbose boot which I could only fix by recreating the swap partition in its original location, setting the new UUID in some config files, then regenerating my boot info.

I must be missing something.  There has to be a way to remove a swap partition.  Any advice would be appreciated.

---

### Post by dearingj on 2009-09-19
You almost had it right. When you do swapoff it disables the use of that swap partition, but the change only lasts until you shut down or reboot. To make it permanent you need to edit /etc/fstab (sudo gedit /etc/fstab) and remove the line which tells Ubuntu to use that partition as swap. After you do that, you can safely delete the partition.

---

### Post by darlinsk on 2009-09-19
Thank you.  That did the trick.  I was thinking of commenting out the swap line in fstab ... but somehow thought it wouldn't be that straight forward.  I should have known!

---

### Post by darlinsk on 2009-09-19
*Sigh*
I spoke too soon.  All seemed well until I actually deleted the swap partition, and resized my extended partition.  I am now back to a funky verbose boot sequence that starts with the message:
Reading files needed to boot.

Thoughts?

---

