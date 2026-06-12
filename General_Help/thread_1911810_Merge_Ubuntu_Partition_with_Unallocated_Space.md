---
title: "Merge Ubuntu Partition with Unallocated Space"
date: 2012-01-19
forum: General Help
---

### Post by saiprem on 2012-01-19
I have Windows and Ubuntu partitions separated by unallocated space.  Please see the screenshot.  Please, in very simple words, someone tell me step by step how to incorporate the unallocated space into my Ubuntu partition.  Windows is on the left and Ubuntu is on the right.  Thank you!

---

### Post by BC59 on 2012-01-19
I recommend you to open a new thread.
In any case to move a partition to the left is difficult and time consuming.

---

### Post by coffeecat on 2012-01-19
@saiprem, it's usually better to start your own thread rather than post to an old one. I've moved your post out into its own thread for you.

---

### Post by HermanAB on 2012-01-19
Short answer: You can't.

---

### Post by saiprem on 2012-01-19
There has got to be a way!:confused:

---

### Post by BC59 on 2012-01-19
The only way is to delete the partitions in the extended and the extended itself. After this the 2 unallocated spaces will be merged. There is no easy way.

---

### Post by CharlesA on 2012-01-19
I thought that you were able to extend an existing ext partition, so that it uses the unallocated space.

Is this not the case?

---

### Post by Cheesemill on 2012-01-19
Easy.

You'll have to use a Live CD so that your partitions aren't mounted, and use it to run gparted.

Extend /dev/sda3 (the extanded partition) to the left as far as possible, and then extend your ext4 partition (dev/sda5) to the left to fill it up.

This will probalbly take several hours to complete.

As always **MAKE SURE YOU HAVE A BACKUP** before messing with your partitions :)

---

### Post by pretty_whistle on 2012-01-19
> **Cheesemill said:**
> Easy.

You'll have to use a Live CD so that your partitions aren't mounted, and use it to run gparted.

Extend /dev/sda3 (the extanded partition) to the left as far as possible, and then extend your ext4 partition (dev/sda5) to the left to fill it up.

This will probalbly take several hours to complete.

As always **MAKE SURE YOU HAVE A BACKUP** before messing with your partitions :)
Several hours?  More like several minutes.  Gparted is quite fast and I did this same operation he's wanting to do.

---

### Post by Dry Lips on 2012-01-19
> **pretty_whistle said:**
> Several hours?  More like several minutes.  Gparted is quite fast and I did this same operation he's wanting to do.

It took several hours for me. But my HDD is a wee tad bigger (1TB). Since the unallocated space is between the two partitions, the data on the partition will be moved to the left, so do what Cheesemill says and do a backup first. I experienced a few broken links afterwards, but nothing serious.

So this is what you'll have to do:

**0.** Backup your data.
**1.** Boot using an Ubuntu LiveCD (or memory stick)
 **2.** Open Gparted (System>Administration>Gparted)
 **3.** Right-click on the swap partition and choose “swapoff”.
 **4.** Select the extended partition, choose Partition>Resize/Move
 **5.** Drag it to encompass the unused space. Click apply (green check)

---

### Post by jetzhou on 2012-01-25
the previous steps worked magic for me. Took a total of 50 minutes on a 250GB hard drive while shuffling about 40GB of space. (I didn't even need to reinstall GRUB as GParted seems to suggest.)

---

### Post by nipunshakya on 2012-01-25
> **saiprem said:**
> I have Windows and Ubuntu partitions separated by unallocated space.  Please see the screenshot.  Please, in very simple words, someone tell me step by step how to incorporate the unallocated space into my Ubuntu partition.  Windows is on the left and Ubuntu is on the right.  Thank you!

seems like you dont have a /home partition and so everything , even your backups are stored in your /. So, instead of extending your partitions, i suggest you to format that unallocated space to NTFS format so that you can use that space as a file sharing option between windows and ubuntu and store your data there. That would be better.

Just  boot to windows, start the disk management utility , if on windows 7, simply right click my computer> manage> there at middle left of window u'll see disk management, click that.
select the unallocated space, right click and simply create a NTFS partition out of it....

Goodluck
Regards,WinuxUser

---

