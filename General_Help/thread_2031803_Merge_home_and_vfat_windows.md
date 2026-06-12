---
title: "Merge /home and vfat /windows"
date: 2012-07-22
forum: General Help
---

### Post by sdglinux on 2012-07-22
Current system is 12.04 with root, swap, home, and windows (vfat) partitions.
I plan to use gparted live cd to delete the vfat partition and then increase the size of /home using the available space left open by the delete - i.e. merge/reformat. 

Will the data in original /home be safe and unchanged?
Upon rebooting Ubuntu, do I need to change anything in 12.04 or will the boot process recognize this partition change allowing me to proceed with "business as usual" but with a larger /home?

---

### Post by oldfred on 2012-07-22
Any system change has some risk. Especially a power failure in the middle. So good backups are important, unless you do not value your data.

That said I have modified partitions many times and not had any issues other than those where I overwrote the wrong partition. Or user error is often the biggest issue.

Only if you old FAT partition is next to your /home will it be easy to do. If FAT is at start of disk and /home at end of disk then you literally have to move all data which then is higher risk.

You can reformat the old FAT partition and mount it as a data partition if you want.

---

### Post by zero2xiii on 2012-07-22
> **oldfred said:**
> 
Only if you old FAT partition is next to your /home will it be easy to do. If FAT is at start of disk and /home at end of disk then you literally have to move all data which then is higher risk.

You can reformat the old FAT partition and mount it as a data partition if you want.
+1

I would also rather recommend this path. Rather use it as a data partition. Much easier, and a LOT safer. Also allows for more options later on.

Cherz

---

### Post by sdglinux on 2012-07-22
I used gparted - deleted vfat /windows and created ext4 /general as a data partition as recommended.  Gparted seemed to run fine and okay; however, the wheels really came off.  I could not reboot Ubuntu. I am getting a message: "filesystem check or mount failed".  Looks like I messed up something bad.  I guess I will have to reinstall Ubuntu 12.04.  I did back up my data prior to gparted.

---

### Post by sdglinux on 2012-07-22
I finally got it working.  I kept searching forum posts and learned that I had to edit the fstab file in the root.  I booted from the 12.04 live CD, mounted the root, and edited fstab to remove /windows (vfat) and add /general (ext4) with the new UUID, name, and type. Saved fstab and rebooted into Ubuntu. My new folder works fine and I am sharing it with the Windows PCs on my network.  Thanks for all suggestions.

---

