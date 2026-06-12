---
title: "Move entire partition"
date: 2011-03-04
forum: General Help
---

### Post by vacco on 2011-03-04
I have an Asus eeePC 1001PX which I have installed Linux to. With a 160 GB hard drive, space is limited, which makes it a problem for me that Asus has chosen to place the 16 GB Windows Recovery partition (which I intend to keep in case of emergency or sale) in the middle of the disk, essentially preventing me from partitioning the disk to my liking with one partition taking up the entire drive (except the space used by the recovery partition.

Is there any way to move the recovery partition to the beginning or to the end of the disk without breaking it?

---

### Post by dabl on 2011-03-04
You can move it with no problem -- the key issue is you don't want to change its sequence number in the partition table.  In other words, if it is currently the second partition on the hard drive, then it needs to stay the second partition -- you need a first partition, no matter how large or tiny.

---

### Post by vacco on 2011-03-04
Any instructions on how to do this would be appreciated. Could I just use gParted and change the amount of Megabytes before and after the recovery partition?

---

### Post by dabl on 2011-03-04
My personal favorite tool for your task is a [[COLOR="Green"]**Parted Magic**[/COLOR]](http://partedmagic.com/doku.php?id=downloads) Live CD. You can also use GParted, including the Gparted on a Ubuntu Live CD.  The nice thing about using a Live CD or USB stick is you don't have to worry about unmounting drives and partitions.

When Parted is showing you the graphic of your hard drive (a horizontal bar with partitions depicted), what you do is shrink partition(s) to the left of your recovery partition, which will free up "unallocated" space.  Just right-click on a partition, choose "shrink/resize", and then your cursor can grab the right end of the partition on the graphic, and pull it to the left. Then you can right-click on the recovery partition, choose "shrink/resize", put your cursor in the middle of that partition, and simply drag the entire partition to the left as far as possible.

When you have the partitions shrunk and moved as you wish, you click the green "Apply" item on the top menu bar, to make the changes to the partition table and drive.

That's as much advice as I can give you, not knowing anything more about your hard drive and partition configurations.  Here's good guidance:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by MestreLion on 2011-03-17
> **dabl said:**
> You can move it with no problem -- the key issue is you don't want to change its sequence number in the partition table.  In other words, if it is currently the second partition on the hard drive, then it needs to stay the second partition -- you need a first partition, no matter how large or tiny.

Hummm, thanks!!! THAT is what i was looking for: a description of HOW the Asus EeePC finds its Recovery partition.

Btw, how did you find this info? Is there *any* documentation about it (official or not?) What are the requirements for the F9 recovery partition to be found by BIOS? Position on partition table, fylesystem type, flags (bootable/hidden), label ?

---

