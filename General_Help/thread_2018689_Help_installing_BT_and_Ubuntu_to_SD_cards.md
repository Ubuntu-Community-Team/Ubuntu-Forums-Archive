---
title: "Help installing BT and Ubuntu to SD cards"
date: 2012-07-06
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-07-06
I am also interested in a similar setup but for different reasons:

I am running ubuntu on a hp dv9000 w/2 500 gb hard drives, duel boot between 12.04 and (eyballing downgrading to 11.04 because its working very well on my eeepc) backtrack 5.

What I want to do is install each os on a separate sd card so running it won't drain so much battery and run faster due to the lack of moving parts (and hopefully run cooler, thing's an oven XD), use 1 hard drive as my home folder + GRUB & not sure about the other one (maybe use it for the backup feature).

I'd like a GRUB entry to load whichever os is on the inserted sd card, so I could swap out when I wanted to switch os's.

Any info would be appreciated!

---

### Post by efflandt on 2012-07-06
Memory card readers on desktops are usually internally USB connected, which the BIOS of computers from at least the past 6 or 8 years (not sure how far back) should be able to boot from.  I can boot from SD in the integral card reader of my HP desktop PC from 2004 (or current 2010 desktop).

But the memory card slot in many laptops is some other sort of block device that BIOS cannot boot, and since grub2 is too big to fit in the mbr, it cannot find the rest of itself on a device not supported by BIOS.  So grub does not even get far enough to display its menu, much less load a kernel with support for the special block device.

So **grub** and **/boot** would need to be on something the BIOS does support like a hard drive, USB flash or drive, or CD/DVD (or floppy disk).

Fortunately the SD slot in my Acer W500P is internally USB connected, so I can boot Ubuntu on SD from grub on it as alternative to Win7 Pro on its SSD.  All I need to also have a different or newer OS is another SD card.

---

### Post by CharlesA on 2012-07-06
Moved to it's own thread.

The original thread is here:
[http://ubuntuforums.org/showthread.php?p=10931854#post10931854](http://ubuntuforums.org/showthread.php?p=10931854#post10931854)

---

