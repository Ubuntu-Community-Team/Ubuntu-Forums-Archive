---
title: "Trouble accessing my Linux partition from Windows 7"
date: 2011-06-10
forum: General Help
---

### Post by Astroe on 2011-06-10
Ok so I'm a recent convert from an all Windows system to Linux, running Kubuntu 11.04 32 bit. But when I'm done with work I like to come home and chill with a video game and Linux doesn't have much of a selection.

So, to the horror of everyone I know, I re-installed Windows and fixed grub so I could dual boot Windows 7 64-bit with my Kubuntu. Got GTA installed and started pwning n00bs.

My problem is that all my music is on the Linux partition but I'd like to listen to it while playing my games. I googled it and found a bunch of shitty little Windows programs that would let me access the Linux partition but there has got to be a way to do it without potentially exposing my box to anybody else.

And I know, this probably belongs in the Microsoft forums but I consider it a point of pride that I have, to date never visited them. Plus the Ubuntu community is way awesomer :p

---

### Post by Quackers on 2011-06-10
One option would be to create a separate NTFS partition and move all your music to that partition. Then both systems could use it :-)
But make sure you don't exceed the 4 primary partitions limit of an mbr partitioned disc! The new partition could be a logical one, instead of primary.

---

### Post by Astroe on 2011-06-10
I like that idea, I could put all my media onto a separate partition and access it from either system, my concern is that this would mean more time spent in Windows and less in Kubuntu, and broken torrents galore if I tried to download straight to the partition..

I was kind of hoping for some way to just mount the Linux bit under Windows. 

Like this, 
mount /dev/sda1 /mnt/Music

---

