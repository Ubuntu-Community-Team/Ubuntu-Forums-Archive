---
title: "Gparted Help"
date: 2012-05-29
forum: General Help
---

### Post by damms005 on 2012-05-29
I want to do a Wubi migration. I used the -c option to check my partitions but I don't have any type 83. I want to format a portion for linux but when I used Gparted GUI to check my device, I see it is all messed up. A lot of useful unallocated FREE SPACES. (the attached image is the present messed-up status of my sda)

1.How can I "extend" the preceeding space to "use up" the unallocated space OR

2.How can I use Gparted to adjust my disk so that the unallocated spaces will be moved to the end and make new logical partition

3. If the above are not possible, how can I format a space for my beautiful linux?

Thanks

---

### Post by damms005 on 2012-05-29
Below is the snapshot of my Gparted GUI. I am using wubi install. How can I allocate those three unallocated spaces? Thanks

---

### Post by Mark Phelps on 2012-05-29
OK, first of all, these are ALL MS Windows filesystem partitions -- and in general, it's a bad ideal to use Linux filesystem utilities to mess with MS Windows filesystem partitions.  So, avoid the temptation to use GParted to mess with these.

Second, you will get more flexibility if you use a third-party Windows partitioning app, than if you try to do this using Windows tools. Since you can't mess with partitions that are in use, you will need to burn a CD image from a file, boot from that CD, and use that to mess with the partitions.

The Windows app I recommend is the Partition Wizard Boot CD.  It's free and can be downloaded from their website.

You should also download and install ImgBurn -- it's a free Windows image burning app.

Once you have those, burn the image to CD.

Then, boot from the CD and do the following:
1) Expand the first NTFS partition to take up the unallocated space
2) You can't do anything with the second space because it's so small that it's likely a partition alignment issue -- and you shouldn't mess with those.
3) Expand the Extended partition to take up the third unallocated space.
4) Expand the last NTFS partition to take up the new space in the Extended partition.

Realize that NONE of these will expand the space allocated to your Ubuntu install because you used Wubi -- which writes to one single file, not to a partition.

---

### Post by coffeecat on 2012-05-29
Threads merged. Please do not start different threads about the same problem.

---

### Post by damms005 on 2012-05-29
Sorry I already messed with sda1 and now when I boot, I get this:

1234F:

Then after pressing everything on my keyboard, I always get the message:

MBR not found
PRESS Ctrl+Alt+Del to restart.

Please my master boot record is messed up but I want NOTHING to happen to my linux apps and files. Pls help.

---

### Post by damms005 on 2012-05-29
Sorry I already messed with sda1 and now when I boot, I get this:

1234F:

Then after pressing everything on my keyboard, I always get the message:

MBR not found
PRESS Ctrl Alt Del to restart.

Please my master boot record is messed up but I want NOTHING to happen to my linux apps and files. Pls help.

---

