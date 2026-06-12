---
title: "Delete other OS to use Ubuntu as primary operating system"
date: 2010-10-15
forum: General Help
---

### Post by theimben on 2010-10-15
I've installed Ubuntu on my netbook on top of Windows XP. And I'm liking it very much :) But how do I delete XP and use Ubuntu as the primary OS from here? Do I have to reinstall it?

Also I want it to delete all the other data just like fresh install on a formatted disk (or as close as).

Thanks

---

### Post by 3Miro on 2010-10-15
How did you install Ubuntu? If you used wubi (from within windows) then you will have to backup all of your data and make a clean install of Ubuntu. 

If you install Ubuntu on a separate partition, then you can just use Gparted to reformat the windows partition and it will kill the other OS. (then in terminal type "sudo update-grub" to get rid of the windows boot option). At any rate, before you mess with partitions, make sure that you have BACKED UP ALL OF YOUR DATA.

---

### Post by theimben on 2010-10-15
That sounds like a good idea. What program can I use to make partitions on windows? And can I install Ubuntu from windows onto that new partition?

---

### Post by 3Miro on 2010-10-15
Windows can make its own partition from Control Center -> Administrative Tools -> Disk Management. In the case of XP it is not very roubust and you cannot resize existing partitions. From Ubuntu and/or Ubuntu Live CD you can use Gparted to manage partitions.

You cannot install Ubuntu on a separate partition from within Windows (at least I don't think so). You boot from a live CD and during the installation process, you can tell Ubuntu to install on that new partition (use manual advanced settings and set the partition as "use as ext4 and mount point /"). You will also need a separate partition for "swap". Make a little bigger than the amount of RAM that you have.

If you want to completely wipe out windows, you should just make a clean install from a live CD and tell Ubuntu to automatically use the entire hard drive (this will repartition everything and destroy windows).

If you don't have much experience with partitions, absolutely make sure that you backup everything important. It is way too easy to mess things up and lose all the data on a hard-drive.

---

