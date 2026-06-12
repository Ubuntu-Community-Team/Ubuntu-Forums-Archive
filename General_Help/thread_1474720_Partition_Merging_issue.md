---
title: "Partition Merging issue"
date: 2010-05-06
forum: General Help
---

### Post by fgbfx on 2010-05-06
Alright, I searched the forums, and made google my friend, but I can't find out how to do this.

I installed ubuntu earlier today, and it installed right beside windows like it usually does, but it apparently didn't give itself enough room for updates on the default settings. So, here's my gparted screen shot

[IMG]http://i26.photobucket.com/albums/c145/fgbfx/gparted.gif[/IMG]
Sorry if that screenie is HUGE.

The most I've gotten toward a solution is formatting the unalocated space and then trying to merge things, which I'm trying now. However, any other help, including details more specfic other than "format the unallocated and then try again" would be awesome.

thanks.

---

### Post by DawieS on 2010-05-06
You don't need to format the unallocated space. You can enlarge your Ubuntu partition by extending it into the unallocated space to the left.

In **Gparted**, click on the **Partition > Resize/Move** tab. You have to grab the extended partition, and drag it to the left until it has the size you want, rounded to nearest cylinder. (You can not really merge partitions).

---

### Post by Mark Phelps on 2010-05-06
Ubuntu won't let you modify partitions that are mounted, and when you're running Ubuntu from the hard drive, the partitions inside your Extended partition ARE mounted.

If you unmount the partitions, Ubuntu won't run because it won't be able to read the files it needs on the drive.

So, you will need to download and burn a GParted LiveCD (get it from distrowatch.com), boot with that, and use that to expand your Extended partition.

---

### Post by Scunnered on 2010-05-06
You can alternatively run Lucid as a LIVE CD and using GParted extend the partition as advised.

---

