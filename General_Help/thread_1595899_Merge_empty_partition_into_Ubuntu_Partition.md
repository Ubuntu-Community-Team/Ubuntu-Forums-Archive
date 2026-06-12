---
title: "Merge empty partition into Ubuntu Partition"
date: 2010-10-13
forum: General Help
---

### Post by aV Echelon on 2010-10-13
Well..after learning how to sync my iPod Touch with Banshee and install Office in wine (works great btw [09]) I have come to the conclusion that Windows is currently useless to me from now on.

Is there any possible way of Merging my formatted Windows partition into the Ubuntu partition without reinstalling? There is 128GB on my Ubuntu Partition and 121GB on my (former) Windows partition and I would rather have more space.

---

### Post by Barriehie on 2010-10-13
> **aV Echelon said:**
> Well..after learning how to sync my iPod Touch with Banshee and install Office in wine (works great btw [09]) I have come to the conclusion that Windows is currently useless to me from now on.

Is there any possible way of Merging my formatted Windows partition into the Ubuntu partition without reinstalling? There is 128GB on my Ubuntu Partition and 121GB on my (former) Windows partition and I would rather have more space.

I would make a backup of the Ubuntu partition and then boot with a gparted live cd and delete the windows partition and then increase the size of the Ubuntu partition, i.e. slide it over the newly deleted partition.  Gparted live cd can be had [here](http://gparted.sourceforge.net/livecd.php).

For the backup I would rsync /home onto a flash drive.

---

### Post by srs5694 on 2010-10-13
Another possibility is to use GParted to create a Linux-native filesystem (ext3fs, ext4fs, XFS, or whatever) over the NTFS partition. You can then mount that partition and use it for your user data files. This approach has the advantage of not moving your partitions, which is inherently at least a little bit risky; but it has the drawback, given your partition sizes, that the size split is a bit awkward.

If you want to move and resize your partitions, you might want to consider shrinking your Ubuntu partition to about 20 GB and then create a new partition to use as /home. (Do a Web search on creating a separate /home partition.) This will be more effort to set up, but keeping /home separate from the root (/) filesystem has advantages, such as the ability to preserve your user data when doing complete re-installations.

---

### Post by Barriehie on 2010-10-13
> **srs5694 said:**
> Another possibility is to use GParted to create a Linux-native filesystem (ext3fs, ext4fs, XFS, or whatever) over the NTFS partition. You can then mount that partition and use it for your user data files. This approach has the advantage of not moving your partitions, which is inherently at least a little bit risky; but it has the drawback, given your partition sizes, that the size split is a bit awkward.

If you want to move and resize your partitions, you might want to consider shrinking your Ubuntu partition to about 20 GB and then create a new partition to use as /home. (Do a Web search on creating a separate /home partition.) This will be more effort to set up, but keeping /home separate from the root (/) filesystem has advantages, such as the ability to preserve your user data when doing complete re-installations.

+1 for the seperate /home.  I've got my /home on an external drive and have managed to carry it across distros/oopses'.  It's well worth the effort, not much, that it takes to make it work.

---

