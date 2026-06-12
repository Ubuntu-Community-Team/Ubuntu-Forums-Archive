---
title: "IS there a way to erase windows partition"
date: 2011-06-02
forum: General Help
---

### Post by watcher6342 on 2011-06-02
i would like to be able to erase my windows partition on my wifes laptop and make the whole thing ubuntu. is there a way for me to do that without losing anything in my ubuntu side and being able to use all of that erased space for ubuntu? i finally have her comfortable enough with ubuntu so she will like to try and learn it. but i am not that familiar with it myself. and dont want to mess it up. thanx in advance..

---

### Post by ruffEdgz on 2011-06-02
One way would be to download a DBAN iso and use that to erase everything you need: [http://www.dban.org/](http://www.dban.org/)

If you have the live CD of Ubuntu already, you should be able to use GParted by going to System >> Administration >> GParted (see screenshot on this post)

Hope this helps.

---

### Post by yetiman64 on 2011-06-02
Delete the partition in gparted (**ONLY if your Ubuntu is installed to its own partition - do not use these instructions if you have a Wubi install**), expand or move and expand the Ubuntu partitions to suit your needs. No need to erase the partition it has to be deleted anyhow.

If you do prefer to do an erase of the data first, you can use the shred command off a live cd.

Use the commands in a terminal,
```
sudo fdisk -l
``` that is a lower case L. This will allow you to accurately identify the correct partition for Windows. Post this output here if you have any concerns, before continuing.

then

```
sudo shred -f -n0 -v -z /dev/sd**XY**
``` where **X** is the drive BIOS letter, and **Y** is the Windows partition number.** It is important not to leave off the Y (partition number) or your complete drive will be erased**.

The switches in use are:
-f = force
-n0 = iterations=0, no wiping passes as the -z switch is in use, this speeds up the erase operation.
-v = verbose output, lets you see the progress of the operation.
-z = zero, does a zeroing pass (resets every bit on the partition to a 0). This is what wipes the partition (or possibly the complete drive if you forget to include the partition number!).

Edit: then use gparted to delete the partition and alter the drive to suit your needs.

As a word of caution, backup all of your important personal data off the drive before resizing/moving partitions on a drive or repartitioning a drive. A failure during the operation can cost you your data. Ubuntu can easily be re-installed from a cd whereas your data needs to be backed up.

One last note while you are using gparted off a live cd. You need to  ensure any partitions being altered aren't mounted or in use, and that the swap partition is turned off (if on, right click the swap partition  and choose "swapoff".

**Edit2**: An alternative to deleting the old windows partition and moving/resizing Ubuntu, you could leave Ubuntu as it is and just reformat the old Windows partition to either a Linux filesystem for storage or even a NTFS storage partition (your preference). This is a much safer route to take as it leaves your current Ubuntu install fully intact and still bootable. Ubuntu will happily boot from anywhere on the drive.

Edit 3: See post below: probably better to take the approach in Edit 2 above to avoid the grub problems possible.

---

### Post by 5149.5 on 2011-06-02
If the erasing/partitioning/etc changes the drive number of the ubuntu partition, it could break grub. Also if grub is on the windows partition, there could be grub problems.

---

### Post by yetiman64 on 2011-06-02
> **5149.5 said:**
> If the erasing/partitioning/etc changes the drive number of the ubuntu partition, it could break grub. Also if grub is on the windows partition, there could be grub problems.

@ 5149.5, please check edits 2&3 in my post above. I agree that deleting the partition may cause a hassle for the OP and have added an alternative. Erasing the partition windows is in won't touch the MBR where grub installs to and the files for grub are in Ubuntu. 

This is all on the assumption **a wubi install is not in use**. In which case Ubuntu resides on the Windows partition itself.

---

### Post by Jennie023 on 2011-06-03
> **ruffEdgz said:**
> One way would be to download a DBAN iso and use that to erase everything you need: [http://www.dban.org/](http://www.dban.org/)

If you have the live CD of Ubuntu already, you should be able to use GParted by going to System >> Administration >> GParted (see screenshot on this post)

Hope this helps.



Thanks! It worked for me

---

