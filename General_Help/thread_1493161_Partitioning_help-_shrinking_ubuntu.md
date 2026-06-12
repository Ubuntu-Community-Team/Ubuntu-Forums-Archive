---
title: "Partitioning help- shrinking ubuntu"
date: 2010-05-25
forum: General Help
---

### Post by AdamMO on 2010-05-25
I currently have a 500gb HDD with a 10gb recovery partition, followed by a 75gb windows parition, followed by a 380gb partition for ubuntu.

Although I didn't expect to, I've already filled up my entire windows partition and am out of space.  Therefore, I'd either like to make a new drive that's visible to both ubuntu and windows, or just increase the size of the windows partition, by, say, 35gb.

My drive currently looks like this:

[ATTACH]158231[/ATTACH]

1. Is there any painless way to increase the size of the windows partition without screwing up ubuntu (using gparted of course).

2. If I were to make a new drive out of the free space on the ubuntu partition, how should it be configured so that it's visible to windows as well as ubuntu while not breaking anything?

Thanks for the help!

---

### Post by geirha on 2010-05-25
See [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition).

Since / is mounted on that drive, you can't do any resizing from the system itself (all partitions must be unmounted, and / is impossible to unmount). Boot your ubuntu cd, the live session has gparted pre-installed. From there you can do the resizing and moving.

---

### Post by jerome1232 on 2010-05-25
Short answer: No

msdos partition tables are stored in the boot sector of it's disk, there's only room in there to store info for 4 primary partitions. In order to have more than 4 primary partitions you can create 1 and only 1 extended partition which can have (15 or 20 I think) partitions inside of it.

You have 4 primary partitions right now, in order to create an extended partition and thus get more than 4 partitions, you will need to delete one of those (preferably the one that's physically last, so Ubuntu, which in turn will kill grub so you better have a live cd handy)

You have an external you can throw backups too?

Edit! Actually now that i think about it, you can shrink ubuntu down, move it towards the end of your disk, and then increase the size of your windows partition, you will need a live cd to do it and it will take a long time.

---

### Post by AdamMO on 2010-05-25
> **jerome1232 said:**
> Short answer: No

msdos partition tables are stored in the boot sector of it's disk, there's only room in there to store info for 4 primary partitions. In order to have more than 4 primary partitions you can create 1 and only 1 extended partition which can have (15 or 20 I think) partitions inside of it.

You have 4 primary partitions right now, in order to create an extended partition and thus get more than 4 partitions, you will need to delete one of those (preferably the one that's physically last, so Ubuntu, which in turn will kill grub so you better have a live cd handy)

You have an external you can throw backups too?

Edit! Actually now that i think about it, you can shrink ubuntu down, move it towards the end of your disk, and then increase the size of your windows partition, you will need a live cd to do it and it will take a long time.

Thanks for the replies!  I've got a gparted boot disk handy, so I could go ahead and try that.  If I move over the ubuntu partition and stretch windows, won't ubuntu no longer be bootable, though?

---

### Post by jerome1232 on 2010-05-25
I believe it will be fine, grub identifies by disk and partition numbers. Keep a live cd in hand just in case you do need to repair grub for some reason.

---

### Post by geirha on 2010-05-25
Keep in mind what the HowToPartition page says
> The Ubuntu installer's Partition Editor, as well as the commonly used GParted partition manager, are some of the safest ways to partition a hard disk. However, it is nevertheless important to back up important files before using them.

And no, it will not break grub.

---

### Post by AdamMO on 2010-05-26
Took a whole 6 hours, but worked like a charm.  Now I have a larger windows partition and a smaller Unbutu partition (I decided to do a 40Gb shift).  Thanks again for the help!

---

