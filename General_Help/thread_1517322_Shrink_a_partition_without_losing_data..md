---
title: "Shrink a partition without losing data."
date: 2010-06-24
forum: General Help
---

### Post by BeWop on 2010-06-24
So, I am completely ubuntu right now, and I need to create a partition for XP without losing all the work I have on ubuntu. How can I shrink ubuntu's partition to make a 15 gb partition for XP without losing data?

According to Gparted:

sda = ubuntu
sda2 = swap
sda3 = extended

---

### Post by Mark Phelps on 2010-06-24
> **BeWop said:**
> So, I am completely ubuntu right now, and I need to create a partition for XP without losing all the work I have on ubuntu. How can I shrink ubuntu's partition to make a 15 gb partition for XP without losing data?

According to Gparted:

sda = ubuntu
sda2 = swap
sda3 = extended

First of all, Ubuntu isn't "sda", it's most probably "sda1".

Second, best approach is to download and burn a GParted LiveCD (which you can get from distrowatch.com), boot from that, and use that to do the partition work.

It's generally easier to install XP first because it's a simpler matter to install Ubuntu afterward, since GRUB can find XP.

But in this case, shrink your sda1 partition to make room, move the other partitions to the left, boot from your XP CD, and install it to the free space.  That will overwrite the MBR, so you'll have to boot from an Ubuntu LiveCD afterward and reinstall GRUB.

---

### Post by wilee-nilee on 2010-06-24
Any resizing always has the danger of losing data. Back it up if you are concerned and use a live Ubuntu cd to shrink the partition. You will have to turn swap off to do this by right clicking on it in gparted. You may also have to possibly remove swap to resize the extended leaving room to install swap again.

---

### Post by oldfred on 2010-06-25
It looks like you have sda4 available as windows will only install to a primary partition sda1 thru sda4.

---

### Post by ezsit on 2010-06-25
Back up your data first! Use gparted from either the live gparted cd or from a desktop edition of Ubuntu running from the CD. Turn off swap and use gparted to shrink and create partitions. Install windows. Use the Ubuntu desktop CD in live mode to reinstall GRUB2.

Or, backup your data, install windows, install Ubuntu, all with a more thought out partition scheme. Second option is easier.

---

### Post by BeWop on 2010-06-25
Got it all done. Thanks for the help

---

