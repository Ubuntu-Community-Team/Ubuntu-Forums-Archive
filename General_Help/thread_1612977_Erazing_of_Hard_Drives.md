---
title: "Erazing of Hard Drives"
date: 2010-11-03
forum: General Help
---

### Post by Robert_P on 2010-11-03
I have built a computer comprising three 160Gb hard drives, each of which had been used as Ubuntu boot disks. I can't remove the Swap partition and some small unallotted partitions. How can I make a total erase of the disks to give me clean starts? Gparted has a tab "Create Partition Table", but I am concerned about turning the disks into expensive doorstops.
Thanks in advance

---

### Post by ivarn on 2010-11-03
Use your live ubuntu cd and while you are in the gui, from the places menu right click on the partitions and lick format.

---

### Post by Robert_P on 2010-11-03
Thanks Ivan, but won't this just clean my partitions rather than cleaning my whole disk in order to rid the old Swap and unallotted partitions? Please excuse a "Newbies" ignorance if this is incorrect.

---

### Post by Quackers on 2010-11-04
In your chosen partition editor click on all the partitions and delete them. In the end the disk will be all unallocated space. You then have a clean disc to do what you want with. The mbr will still have bootloader stuff in it but that will be over-written as soon as an OS is installed.

---

### Post by t0p on 2010-11-04
> **Robert_P said:**
> Thanks Ivan, but won't this just clean my partitions rather than cleaning my whole disk in order to rid the old Swap and unallotted partitions? Please excuse a "Newbies" ignorance if this is incorrect.

If you run GParted (**System > Administration > Partition Editor** I think) from the live CD, you will be able to unmount all the partitions on your hard drives, then format the drives and re-partition them however you like.  This will, in effect, completely "erase" the drives, and you'll be able to start over.

Of course, make sure you back-up any data that you think you want/need to keep.  Good luck.

---

### Post by dcstar on 2010-11-04
> **Robert_P said:**
> I have built a computer comprising three 160Gb hard drives, each of which had been used as Ubuntu boot disks. I can't remove the Swap partition and some small unallotted partitions. How can I make a total erase of the disks to give me clean starts? Gparted has a tab "Create Partition Table", **but I am concerned about turning the disks into expensive doorstops.**


Do not be concerned, all this will do is make the disk like a brand new fresh unit from the factory - awaiting you to install an OS or create partitions as you like.

Just "Unmount/Swapoff" any partition in use as advised in other posts.

---

