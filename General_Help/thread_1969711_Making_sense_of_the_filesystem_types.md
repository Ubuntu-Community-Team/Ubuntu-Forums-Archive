---
title: "Making sense of the filesystem types"
date: 2012-04-30
forum: General Help
---

### Post by raen on 2012-04-30
Hello. I'm trying to optimize a dual-boot setup of Precise and Windows 7, with the intention of sharing documents. I have 8GB of RAM and an 8-core 3.1GHz CPU. No RAID. No server. Just personal home use, although I do intend to install many different DEs for variety.

Each system is on its own 1.5TB SATA HDD. I'm considering allocating Ubuntu as follows:
/dev/sda1 /(root) 200GB
/dev/sda2 /home 1.3TB
/dev/sda3 swap ??? (2GB? 4GB? 8GB? 16GB? Don't bother?)

My conundrum is that I'm not sure whether to use ext3, ext4, xfs, or something else. I've Googled around, but even when I could find something less than three years old, I only ended up confused and overwhelmed with a lot of technical information.

Can someone give me a "for idiots" breakdown or recommendation?

Thanks,
raen

---

### Post by pqwoerituytrueiwoq on 2012-04-30
200gb is way more than root needs 10gb would be plenty
just use ext4 (be sure to use noatime in fstab for these when they are on SSDs)
if you care about hibernate give swap 8.5gb personally i would just suspend if i had even 4gb on my ram i am not waiting for 4gb to write to swap to enter a lower power state i will be bring in it out of in 30 min anyway

---

### Post by raen on 2012-04-30
> **pqwoerituytrueiwoq said:**
> 200gb is way more than root needs 10gb would be plenty
just use ext4 (be sure to use noatime in fstab for these when they are on SSDs)
if you care about hibernate give swap 8.5gb personally i would just suspend if i had even 4gb on my ram i am not waiting for 4gb to write to swap to enter a lower power state i will be bring in it out of in 30 min anyway

I know the system itself has a small footprint, but I like to have wiggle room to install a metric boatload of things.

I don't plan to hibernate or suspend.

I have no idea what noatime is and I've yet to explore fstab, although I may need to do that soon to help set up my dual boot. I don't have any SSDs, just HDDs.

May I ask why you recommend ext4 over the other options? That's my primary question here.

Thanks,
raen

---

### Post by lykwydchykyn on 2012-04-30
> **raen said:**
> I know the system itself has a small footprint, but I like to have wiggle room to install a metric boatload of things.

200GB root isn't wiggle room, it's more "flail around wildly" room.  I've never seen a root partition go past 20 GB, even when I installed big games, multiple desktop environments, etc.

It's your disk space, of course; use it as you see fit.
> 
I don't plan to hibernate or suspend.

Honestly, I would not even create a swap partition.  If you discover you've run out of 8 GB of RAM, you can create a swap file and add it later (linux can swap to partitions or files, it doesn't care).

> 

I have no idea what noatime is and I've yet to explore fstab, although I may need to do that soon to help set up my dual boot. I don't have any SSDs, just HDDs.

'noatime' is a mount option.  Normally, every time you read a file, the filesystem records the timestamp as the files "atime" (access time).  Since this is basically a useless metric, and involves a degree of overhead, it makes sense to turn it off.  This is what noatime does.

> 
May I ask why you recommend ext4 over the other options? That's my primary question here.


I'd recommend ext4 simply because it's receiving the most active development of any of the options.  btrfs is being actively developed, but many say it's not ready for primetime.

Ext3 isn't bad, but my (limited) understanding is that it lacks some extent-based storage which is supposed to be more efficient for really large files.

Ext2 lacks journaling, I wouldn't use it on any filesystem I care about. 

XFS -- been a long time since I used it, and I get it confused too much with JFS, to be honest.  So I won't comment on it.

---

### Post by hal8000 on 2012-04-30
You can read all about ext4 here:

[https://wiki.archlinux.org/index.php/Ext4](https://wiki.archlinux.org/index.php/Ext4)

It is the latest evolution of the extended filesystem.


Option noatime speeds up access to the filesystem as time and date stamps not updated

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

Once again, 200G is far too big for a / partition. A full system even  with loads of source software is much less than 20G.


ext4  filesystem is journalled and as such very little file fragmentation exists. Used every single day my 6G / partition had a mere 1.6% fragmentation in 6 years!! Windoze by contrast has about 14% fragmentation after installing.

---

