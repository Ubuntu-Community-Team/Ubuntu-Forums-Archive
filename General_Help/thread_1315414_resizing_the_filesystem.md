---
title: "resizing the filesystem"
date: 2009-11-05
forum: General Help
---

### Post by bjaz on 2009-11-05
hello all
I'm trying to download upgrades, yet the file system size is too small. but i still have free space on others partitions
I've been trying to increase the filesystem partition size using gparted but i can't quite figure out how this work. I can increase the part sizes but the file system size seems to stay the same...

what should i try ?
thanks

ben

---

### Post by beastrace91 on 2009-11-05
You cannot adjust the size of mounted (active/in use) partitions. To resize your main Ubuntu partition you will need to run gParted off a live CD or USB drive to do this.

Regards,
~Jeff

---

### Post by Mark Phelps on 2009-11-05
> **bjaz said:**
> hello all
I'm trying to download upgrades, yet the file system size is too small. but i still have free space on others partitions
I've been trying to increase the filesystem partition size using gparted but i can't quite figure out how this work. I can increase the part sizes but the file system size seems to stay the same...

A filesystem doesn't have a "size"; instead, it occupies one or more partitions -- each of which DOES have a size.

To increase the size of one partition, you have to shrink, and sometimes move, another partition to create unallocated space.

If a partition is mounted at the time, you can not change its size. So, you have to unmount it first.

---

### Post by P4man on 2009-11-05
+ you may have to right click your swap partition and select swapoff before you can resize extended partitions that contain a swap partition

---

### Post by bjaz on 2009-11-06
thanks for your answers.
it finally worked in gparted, I was just focusing on the wrong partition.

since we're on the subject, I now have three installs on the disk, and would like to keep only one (Ichose the install side by side option), and my wife's japanese windows XP.

can I just delete the unwanted partition in GParted and attribute the space to the remaining one ? i'm afraid of the consequences this might have on the grub / boot loading sequence.

the install boot partition I want to keep is the first in the grub

thanks again

ben

---

### Post by P4man on 2009-11-06
if you are using grub2, it uses UUIDs to identify partitions and you should be ok. Grub1 might get confused if you delete move and resize partitions. Either way, booting a livecd and rerunning update-grub ought to solve it should you encounter problems.

---

