---
title: "Files are &quot;gone&quot; but Disc Usage is the same???"
date: 2010-09-01
forum: General Help
---

### Post by neu5eeCh on 2010-09-01
Long story short: I reinstalled Ubuntu.

On previous installation, my "home folder" was on a separate partition.

After I reinstalled, everything in my old desktop folder (despite being on a separate partition) was gone...

Every other folder, however, remained intact?

It gets weirder. One of the folders in the original desktop folder was a copy of my IPOD music collection, It took up almost 80 gig of space. Strangely, the disc usage hasn't changed after reinstall. You would think that if the files had been deleted after re-install, there would be much more space on the partition. But that isn't the case. It's as if the folder were still there but invisible (and not hidden).

What's up?

Fortunately, I have backups of everything. But what do I do? And why did the reinstall "delete" everything in the desktop folder when it was on a separate partition? And if it didn't? Where is it?

And is it worth trying to sort out? Should I just reformat the partition and restore?

---

### Post by Cypress421 on 2010-09-01
Did you reinstall Ubuntu into a partition or clean installed the whole disk?

---

### Post by neu5eeCh on 2010-09-01
I did two things: First, I tried re-installing Ubuntu without formatting (the relevant partition). 

When that didn't produce the desired results.

I did a complete clean reinstall (reformatted relevant partition and reinstalled).

---

### Post by tbohaning on 2010-09-02
Try this at a command prompt:

fdisk -l

This will print out a list of your configured devices. For example, mine looks like:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5438

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25         997     7815622+  82  Linux swap / Solaris
/dev/sda3             998        7076    48829567+  fd  Linux raid autodetect
/dev/sda4            7077       60801   431546062+  fd  Linux raid autodetect

Then review /etc/fstab and see if all of the devices are mentioned in the  file. I suspect that you will find your old home partition unmounted. If so, you can add it to the fstab and all of your old data should return.

Terry

---

