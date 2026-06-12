---
title: "combining partitions"
date: 2010-03-14
forum: General Help
---

### Post by mIXpRo on 2010-03-14
hii, 

i have ubuntu jaunty 9.04 on a partition windows 7 on another partition , and another partition for storing files as a backup if something happends to windows :mad: .
so i got sick of windows and i want to combine the 3rd partition to ubuntu , anyone knows how ? 

thnks in advance .

---

### Post by karthick87 on 2010-03-14
Try Gparted..
```

sudo apt-get install gparted
```

---

### Post by mIXpRo on 2010-03-14
how do i use it ?

---

### Post by DawieS on 2010-03-14
The first thing you have to do in **gparted**, is to select the right disk in the top right-hand corner (/dev/sda or /dev/sdb etc). You will recognize it by the size, as well as the partition names, displayed in rows in the middle.

Now if you click on the graphical bar representing the total disk, you will see the highlighted partition name/type/size, in the rows below, on which you clicked.

You can only work on **unmounted** partitions. If you plan to work on your boot partition, you should boot from the Live CD, and use **gparted** from there.

To delete a partition, right-click on it and select **Delete**. Now click on **Apply**. This will delete the partition (and contained data) and insert unallocated space.

You can resize the partitions to the left and right of the unallocated space, to extend into the unallocated space. You can also shrink existing partitions (provided your contained data will still fit).

After you have completed selecting your chosen actions, click on **Apply**, to finalize the actions. Moving and resizing can take quite some time.

If you have a power failure during this time, you will probably end up with a partially corrupted disk. It is always best to back up all your important data, especially those that you cannot replace (eg. digital photo's or movies and project work).

If you are planning to resize **NTFS** partitions, you should first **defrag** it a few times in Windows, to make the task at hand easier for **gparted**. Also run **chkdsk** to ensure integrity. **Gparted** refuses to touch **NTFS** partitions if there is a slight problem.

If you do not use the **hibernate** facility, and have 2 GB or more RAM, I would recommend not having a **swap** partition. You might as well use that disk space more productively, and Ubuntu will run just as fast.:grin:

---

### Post by Rocket2DMn on 2010-03-14
It is important to note that you cannot "merge" partitions.  As DawieS has explained in his detailed directions, you will need to delete on partition, then grow a neighboring partition into the newly opened space.  Please be sure you move all the data on the partition to be deleted to another area (like an external hard drive) so you can move it back after your partition editing.

---

### Post by mIXpRo on 2010-03-14
thnks everyone for the info

---

### Post by EvCrock on 2010-06-09
ummmmmm..... this may be a lot easier than I'm making it, but how do you boot from the live CD?

---

### Post by PGScooter on 2010-06-09
> **EvCrock said:**
> ummmmmm..... this may be a lot easier than I'm making it, but how do you boot from the live CD?

to boot from the live CD, just insert the CD into the drive and restart. Your CDROM has to be high on the boot-order or you have to access the boot menu (F12,DEL, etc).

Did this do it?

---

