---
title: "Help: Understanding partitions and editing/resizing them"
date: 2012-07-15
forum: General Help
---

### Post by Ordep_ on 2012-07-15
It was a while ago when I did the partition on my Win7 laptop to install Ubuntu so I don't remember well how I did it but I do remember that I made a mistake and assigned 40GB to swap instead of just 4GB.Anyways, my Ubuntu side is filling up by making backups of all my work,media, and others because I'm moving soon and only want to take my laptop with me.

 Is there anyway that I can claim (move,edit) part of those 40GB from swap into my Ubuntu side?

 Also why is it showing sda5(/) and sda6(/home)? Can I access that space in sda5? Where? How? (the picture from gparted is attached)

 I'm assuming sda2 and sda3 are the Windows side, I don't want to mess with that since I know it could be trouble later on that side.

 My main goal here is to increase my memory in Ubuntu(sda6) by taking some from the swap (sda4) or from sda5 (/) ... unless that actual memory on sda5 is available then I'd like to learn how I can access it.

 Also and most important.. If I can resize those, am I going to lose any data or there is a risk for it? Because if that's the case I'll just get an external HD. Got too many Grad School/dissertation files here to risk throwing my career away in a computer error

Attached is a picture from gparted







 Thanks in advance for ny help.:D

---

### Post by oldfred on 2012-07-15
You will have to use a liveCD or USB to modify partitions. And liveCDs usually mount swap to speed things up, so you usually have to click on swap and swap off to unmount the swap from the liveCD. The little key symbols show the mounted partitions.

I do not like moving partitions left but you can. When you do that it has to copy all data to move it and it can be slow. And interruption or power failure will corrupt data so be sure to have good back ups.

Part of the issue of swap is that it is primary partition, but all the Linux partitions are inside the extended. You can shrink swap and move extended left, then move sda5 left.

I normally make my / partition only 25GB, but have all data in either shared NTFS partition for use with Windows (still there even though I do not boot XP hardly at all) and a /mnt/data partition for most of my data. Data may not be on same drive as my system and I have several systems so I want to use data in all of them.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Expanding an Ubuntu System Partition and related info:
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by F W Adams on 2012-07-15
You certainly need to boot from a live CD to start messing with moving partitions. Also the thing to remember is that it's dangerous, a mistake can be very costly. I would see it as essential to buy or borrow a usb drive and make backups on that. It's always a good idea to have backups off the machine anyway, backups on the machine don't protect you from losing the whole thing.

You have a huge spare space in /dev/sda5, the system partition is not going to get much bigger, you could keep 13 GB for that and then make another partition of 148GB. You could mount that so that it is accessible from /home/userxx, perhaps on a directory /home/userxx/additions.

Couple of other things, if you format a partition ntfs it can be accessed by both Windows and Ubunu, could be useful?

And to tell people about your setup the usual way is to send the output of "sudo fdisk -l", with an el, not a one.

---

