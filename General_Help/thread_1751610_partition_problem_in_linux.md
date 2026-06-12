---
title: "partition problem in linux"
date: 2011-05-06
forum: General Help
---

### Post by velt on 2011-05-06
Hi im running the latest ubuntu on an old acer of mine. I got into the issue myself, i use to have win xp on this machine, but thn when i moved to ubuntu i did something wrong with the partition system. 
now im trying to use gparted esentialy to fix it. 
I will show you in this screnshot that i have two main patitions, well i would like to merge the /dev/sda4 to my "main" partition called sda5. 

Im a newb, i dont know why is so hard to manage partitions in linux, it was quite straight forward in windows. I just want some order in my disk

[[IMG]http://img195.imageshack.us/img195/5787/gpartedi.png[/IMG]](http://img195.imageshack.us/i/gpartedi.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by HereInOz on 2011-05-06
First up, you won't be able to do anything while using GParted inside the Ubuntu system, as the partitions are mounted and you can't touch them.

Download an iso of GParted and burn a CD from it, then boot the machine from that CD, and this will allow you to get to the partitions and work with them.  Same as in Windows - you can't repartition a drive which is actively involved in the system.

You then need to make sda4 smaller from the right, and put the swap partition and sda3 over to the right of sda4.  You can then expand sda4 to take up any unused space to its right, then merge sda4 with sda5. Bear in mind that I have never done exactly what you want to do, and you may run in to trouble merging a primary partition with a logical partition.

You can but try.

Remember, if it breaks, you may lose everything, so take a backup of all you need beforehand, and be prepared to re-install if events turn to straw.  Re-partitioning can do that to you.

---

### Post by velt on 2011-05-06
> **HereInOz said:**
> First up, you won't be able to do anything while using GParted inside the Ubuntu system, as the partitions are mounted and you can't touch them.

Download an iso of GParted and burn a CD from it, then boot the machine from that CD, and this will allow you to get to the partitions and work with them.  Same as in Windows - you can't repartition a drive which is actively involved in the system.

You then need to make sda4 smaller from the right, and put the swap partition and sda3 over to the right of sda4.  You can then expand sda4 to take up any unused space to its right, then merge sda4 with sda5. Bear in mind that I have never done exactly what you want to do, and you may run in to trouble merging a primary partition with a logical partition.

You can but try.

Remember, if it breaks, you may lose everything, so take a backup of all you need beforehand, and be prepared to re-install if events turn to straw.  Re-partitioning can do that to you.

thanks i have already lost all my data a couple of times so yeah, dont worry i dont have anything left in this machine. i will give this a try.

---

