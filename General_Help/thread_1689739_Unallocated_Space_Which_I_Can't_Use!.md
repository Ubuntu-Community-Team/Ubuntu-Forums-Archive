---
title: "Unallocated Space Which I Can't Use!"
date: 2011-02-17
forum: General Help
---

### Post by MysteryPig on 2011-02-17
After installing Windows 7, and shrinking my Ubuntu 10.04 partition, I can't expand my Windows 7 Partition. I see that it is inside of "extended", but I have no idea of how to get it out, and use it to expand my Windows 7 Partition. Here is a screenshot (I'm using a live CD) Also, I want to know why Windows 7 is called Windows XP in gparted, and how to change that.
[IMG]http://i52.tinypic.com/aw9nyf.png[/IMG]

---

### Post by Mark Phelps on 2011-02-17
Windows 7 is NOT inside the Extended partition, it precedes it. So, there's no reason to get it out -- it already is.

As to moving the Ubuntu 10.04 partition out, you basically can't do that in one step.  You would have to do the following:
1) Back off the Ubuntu partition to an external drive
2) Shrink the Extended partition to the right
3) Create a new Ext4 partition in the unallocated space
4) Copy the contents of the old Ubuntu partition into the new one

And you can't do this from Ubuntu because it needs that partition mounted in able to run.  You would have to do this from a LiveCD -- but then, be sure that no partitions are mounted.

To change the partition label that you see in GParted, you can do that in GParted itself.

---

### Post by Sean Moran on 2011-02-17
> **MysteryPig said:**
> After installing Windows 7, and shrinking my Ubuntu 10.04 partition, I can't expand my Windows 7 Partition. I see that it is inside of "extended", but I have no idea of how to get it out, and use it to expand my Windows 7 Partition. Here is a screenshot (I'm using a live CD) Also, I want to know why Windows 7 is called Windows XP in gparted, and how to change that. 
Certainly not pretty at all.  

Simplest way might be to just create a new partition in the extra space, make it FAT32 or NTFS, so that Windows can read it, and put your data on that.  Resizing is long and slow, but by the look of it, you're going to get a good lot of practice at resizing partitions in the near future.  Good luck mate.

---

### Post by plucky on 2011-02-17
> After installing Windows 7, and shrinking my Ubuntu 10.04 partition, I can't expand my Windows 7 Partition. I see that it is inside of "extended", but I have no idea of how to get it out, and use it to expand my Windows 7 Partition. Here is a screenshot (I'm using a live CD

Remember you have to turn swap off before you can do anything with the extended partition (even on the Live CD).

You should then be able to shrink the start of the extended partition.

Use Windows 7 disk management tools to expand the windows partition.

**Back up first**

Good Luck

---

### Post by MysteryPig on 2011-02-17
> Remember you have to turn swap off before you can do anything with the extended partition (even on the Live CD).

How do I turn off swap?

---

### Post by wilee-nilee on 2011-02-17
> **MysteryPig said:**
> How do I turn off swap?

Right click on it, the text portion and swap off.

---

