---
title: "Change NTFS partiton to Linux partiton"
date: 2012-02-10
forum: General Help
---

### Post by Unotforme on 2012-02-10
Hello everyone,

I recently installed 11.10 (64 bit) as a dual boot alongside Vista. I'm new to Ubuntu, and I must say I'm really impressed with Ubuntu. Struggling a little with the Unity thing, but definitely getting more comfortable as time goes on.

My question is this:

I have a Acer AMD 64 Quad Phenom 9550 2.2 GHz with 8 GB Ram. I have Vista installed on one 640 GB drive and Ubuntu installed on a second drive of 750 GB. When I installed Ubuntu I allocated about 150 GB to it, and the rest of the drive (about 600 GB) to NTFS, not really realizing what I was doing. I would now like to delete the 600 GB NTFS and give it to Ubuntu. The 600 GB partition has nothing on it. Do I just use Gparted to delete the NTFS partion and reassign it to Linux using Ext(?) Attached is a screen shot from Gparted.

---

### Post by savanna on 2012-02-10
First of all, *back up your data* on the Linux partition.

Since you're using an extended partition, things could get messy. Rather than deleting sdb2 I suggest you just shrink it to the minimum size the tool will allow. Then expand sdb5 to take up the free space.

---

### Post by hwttdz on 2012-02-10
Not so familiar with extended partitions, so removing my response.

---

### Post by QIII on 2012-02-10
... or ...

Leave it as is and use it as a common data partition.

With a large drive I often carve out just 250 GB or so for Linux and leave the rest as NTFS.   150 GB is plenty of room for Linux and you keep the rest of the hdd visible to your Windows installation.

Don't worry about it now.  When you upgrade to the next version, back up your important stuff and do a fresh install.  Do what you want with the drive then.

---

