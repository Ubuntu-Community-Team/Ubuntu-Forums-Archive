---
title: "Scratching My Head."
date: 2011-11-17
forum: General Help
---

### Post by RyanRage on 2011-11-17
So, you're probably not astonished to see another

"Error: No Such Partition.
grub rescue>"

post on here.. but please don't dismiss right away, i did this one in pretty good, lol. In advance, please, no geek talk.. As basic English as humanly possible.

Started out using dual windows7/ubuntu boot.
Loaded up ubuntu with updates and for some reason, it would lock up at the start screen of ubuntu where you go to type the password in. I figured no big deal, I'll just wipe out the whole hard drive as I don't use windows on this computer anyway and i'll just reload ubuntu up as the base os (Keep in mind, I do not have ANY disks to back the computer up, never really needed any because I used it only for basic stuff). So after deleting the partitions using fdisk in the command prompt.. Wham, I get this message.

So my question is.. What now?

---

### Post by Mark Phelps on 2011-11-17
You most probably installed GRUB to your disk MBR during your dual-boot setup.  When you removed the partitions, you removed the actual boot loader files, so now, GRUB has nothing to hand over control to!

Simply boot from an Ubuntu desktop CD, go through the normal installation, and all that will be fixed.

---

