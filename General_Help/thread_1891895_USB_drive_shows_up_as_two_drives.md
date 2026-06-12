---
title: "USB drive shows up as two drives"
date: 2011-12-06
forum: General Help
---

### Post by Mars11 on 2011-12-06
Okay, so this USB drive that I got shows up as two drives. I know this isn't two partitions, one drive is very small and write protected. How would I fix this?

---

### Post by mörgæs on 2011-12-06
You didn't mention the name. Is it a USB stick from San, and does it contain U3 software?

---

### Post by Mars11 on 2011-12-06
No, it's unbranded. I also know it's not a U3 drive because I've owned a few.

---

### Post by Mark Phelps on 2011-12-07
How do you KNOW the USB drive doesn't actually contain two partitions (not "drives")?

Open a terminal and do a "sudo fdisk -lu" (lowercase L, not a one).  That will list out all the partitions, including any that might be "hidden" -- and we can see what IS on the "drive".

---

### Post by Mars11 on 2011-12-07
> **Mark Phelps said:**
> How do you KNOW the USB drive doesn't actually contain two partitions (not "drives")?

Open a terminal and do a "sudo fdisk -lu" (lowercase L, not a one).  That will list out all the partitions, including any that might be "hidden" -- and we can see what IS on the "drive".
Because one "partition" is sdc while the other sdd. Partitions don't do that.

---

### Post by dcstar on 2011-12-08
> **Mars11 said:**
> Because one "partition" is sdc while the other sdd. Partitions don't do that.

USB makers deliberately create their devices with CD-emulation (for Windows) that can look like another device.

Use gparted to wipe the device(s) by creating a new partition table.

---

