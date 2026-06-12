---
title: "Move Installation"
date: 2009-11-10
forum: General Help
---

### Post by waspbloke on 2009-11-10
I have Ubuntu installed on my eSata drive and Vista on my internal drive. Grub won't play nicely if the eSata isn't plugged in at boot.

What I want to do is copy the partition with ubuntu onto the appropriate free space on my internal drive, modify grub and hopefully everything will be sweet.


Is it as simple as that or will I run into any other problems?

Any help or advice would be great.

---

### Post by undecim on 2009-11-10
Easiest thing would be to backup your files and reinstall on the new drive.

But if you want to move the partition without reinstalling, you will need to do 4 things:

1: make the new partition(s)
2: move the files from the old partion to the new partition
3: edit /etc/fstab accordingly
4: edit your grub config to boot the new partition

You should be able to do all this from a live CD

Use gparted for making the partitions.

To move/edit files, press alt+f2 and type "gksu nautilus" this gives you nautilus in root mode, which lets you move, edit or delete any files without permission errors (be careful here!)

If you need me to be more specific anywhere, let me know. I'm pressed for time at the moment, otherwise I'd elaborate, but I will check back later.

---

### Post by waspbloke on 2009-11-11
Thanks for the reply.

I shall do this tomorrow. I'd forgot about fstab - d'oh!

I'll post back (hopefully) when it's done.

---

