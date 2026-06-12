---
title: "File Transfers to new HDD?"
date: 2009-12-11
forum: General Help
---

### Post by black28 on 2009-12-11
since my HDD is only a 60GB, if i were to buy a bigger HDD how could i take all that is on the HDD including the Operating System and all files and Move it to the bigger one so that i can swap it out and run from the new one?

---

### Post by audiomick on 2009-12-11
My guess is, install it, set up partitions with gparted, and copy.
I think you would have to install grub to the new HD in order to boot from it.

also, look at clonezilla:
[http://en.wikipedia.org/wiki/Clonezilla](http://en.wikipedia.org/wiki/Clonezilla)
[http://www.clonezilla.org/](http://www.clonezilla.org/)

I think I read that this is one of the things it can do.

---

### Post by soulsource on 2009-12-11
In general: yes

But: You have to fix your /etc/fstab and the grub config (I don't know anything about how to do this in grub2) to reflect your new partition layout.

---

### Post by john newbuntu on 2009-12-11
I am guessing that you could use rsync or dd to copy the partition data over.  MBR on the new disk needs to be updated to with grub2 data for the new disk.  And of course the block ids in /etc/fstab of the new disk.
If you are on a PC and use the new HDD as a secondary, I would imagine that after making these changes, you could change BIOS to boot from the secondary first to try things out before swapping.  Someone please correct me here if this is a bad idea.

---

