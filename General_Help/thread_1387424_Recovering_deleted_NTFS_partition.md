---
title: "Recovering deleted NTFS partition"
date: 2010-01-21
forum: General Help
---

### Post by mohtasham1983 on 2010-01-21
Hi,

A while ago I made an image of Ubuntu on my flash drive. Yesterday, I was trying to format it using my Arch Linux machine. I was in rush for no reason. I followed a tutorial which explained the process using fdisk. I'd worked with such utilities before, so I had too much confidence about myself. So ran fdisk -l, and because my windows vista partition (sda1) was showing as NTFS, I thought it was my flash drive partition. So I ran the following:

[PHP]fdisk /dev/sda1[/PHP]

I pressed d for deleting the partition. If I recall correctly, it gave me some numbers and I picked 1. Then I was going to create a new partition by pressing n. Then it asked me for primary or logical. I chose primary, it told me no free space. Then I chose logical and it worked. Based on the tutorial I was following, at this step I had to format my partition, so I issued the following command:

[PHP]mkfs.ext3 /dev/sda1[/PHP]

It told me that the device was busy. I tried to unmount it, but it said the device was not mounted. Then I removed by flash drive and connected it again, but all of a sudden I saw all my files in it. Then I realized what I'd done. 

Tried to mount /dev/sda1 to some directory, but it was mounting something like a linux file system directory structure to that directory and its size was equal to my home directory.

Anyways, I thought my windows Vista and over 100 movies I had on that partition were not a big deal. But when I was leaving the house, I realized I had more than 500 pics of my parents's trip to San Francisco there. That's why I'm desperately looking for a way to recover my pictures before my mom kills me. 

The good thing is that deleting my partition using fdisk was done immediately in one second and didn't take a long time. I wasn't able to format that partition, either. That is, I think I still have high chance of recovering the pictures. 

I found a tool called TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) which seems to be able to solve my problem, however, I'm not quite sure if it works. I don't want to damage my data using a software that I cannot trust. I was wondering if anyone has ever used this tool or any other tool that can recover the data? 

Thanks in advance,

PS. Always, make several backups of your important data, especially your valuable pictures.

---

### Post by michy99 on 2010-01-21
Testdisk is probably your best bet. This page can walk you through it.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by mohtasham1983 on 2010-01-21
I will try it tomorrow when I'm back home. Hopefully I can recover all my files.

---

### Post by Leppie on 2010-01-21
if you really haven't formatted the partition, it may be fully recoverable.
search for boot images like Hiren's Boot cd.

if you can't recover the partition, testdisk comes with photorec which can pull files from lost partitions.

---

