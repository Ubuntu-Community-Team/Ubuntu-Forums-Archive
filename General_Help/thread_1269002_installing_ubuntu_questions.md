---
title: "installing ubuntu questions"
date: 2009-09-17
forum: General Help
---

### Post by jsarran on 2009-09-17
I use to run ubuntu on my old desktop about a year ago then I bought a new one and had winblows vista on it. Now I want to put ubuntu on it but i'm not familiar with the procedure of *partitioning a hard disk, and installing ubuntu. if anyone can let me know what to expect when booting from disk

in addition i am going to install another hard disk to install ubuntu sever on it. is this possible? I mean i can dual boot right?

*I'm not 100% of the meaning of partition if any can enlighten me, that would be wonderful!

yeah i am aware of my ignorance, im not a ubuntu guru

---

### Post by pricetech on 2009-09-17
So are you planning to dual boot vista and Ubuntu or wipe vista out and use Ubuntu exclusively ??

---

### Post by itsjareds on 2009-09-17
A partition is basically a "divider" in a hard disk that acts like another hard drive. This allows you to format your hard disk with two different filesystems. Partition 1 could be NTFS and partition 2 could be EXT3, all on one disk! This is a useful way of keeping your Windows and Linux OSes separate, while only using one hard drive.

[http://en.wikipedia.org/wiki/Disk_partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning")

And, before you start partitioning, we need to know if you're removing Windows Vista and replacing it with Ubuntu, or if you just want to dual boot Vista and Ubuntu (and Ubuntu Server). You don't necessarily HAVE to get a separate hard drive to install Ubuntu Server on because you can partition your first drive :)

---

### Post by gadolinio on 2009-09-17
Partitions act as if they were separate hard disks, virtually speaking, while they are part of the same physical device.
To install ubuntu in a partition for its own, boot your computer with a liveCD. Go to system-->administration-->gparted partition editor (at least in Intrepid Ibex, gparted is included in the liveCD). There, you'll have a very easy-to-use program to manage your partitions. Right click a partition to see what you can do to it, like resize, format, etc. Navigate the menus. There's a graphic representation of your hard disk drive at the moment, and it changes when you propose some modification (which is still not effective). I dual-boot windows xp and ubuntu intrepid ibex; i kept the original NTFS partition for windows, created a new 3ext-one for ubuntu, and another NTFS for data storage.
Just use the program to see what you can do with it; until you click the button saying "apply", nothing of what you do will actually happen. So you can try using the program without doing any harm to your computer, if you avoid applying changes. If something "goes wrong", close the program and refuse to keep the sketched changes. Then open gparted again.
Once you're happy with the changes, click apply.
After having partitioned your disk, close gparted and double-click the "install" icon in the live_session_user's desktop. And just follow the steps, choosing to install ubuntu in the partition of your choice.
Hope you find this useful...

---

### Post by gadolinio on 2009-09-17
> **pricetech said:**
> So are you planning to dual boot vista and Ubuntu or wipe vista out and use Ubuntu exclusively ??

Good point. If you want to get rid of windows you might well delete its partition with gparted, and then assign that space to another one; or format the partition and install the other ubuntu there; or use it for data storage.

---

