---
title: "All OS Question:  Supplies needed to safely partition hard drive*"
date: 2009-09-27
forum: General Help
---

### Post by Dullstar on 2009-09-27
*I don't have an external hard drive to back up onto

Anyways, my brother won't help me with something I really want to do, and that is partition my hard drive.  You see, I want to experiment with different operating systems and Linux distros, but I can't until my hard drive is properly partitioned.  So what do I need to safely partition this hard drive so I can move on with my life (preferably with alternatives to the external hard drive.

110 gigs of data need to be backed up, minus the size of Windows.  This also does not include anything that I do not want and also don't need.

---

### Post by oboedad55 on 2009-09-27
> **Dullstar said:**
> *I don't have an external hard drive to back up onto

Anyways, my brother won't help me with something I really want to do, and that is partition my hard drive.  You see, I want to experiment with different operating systems and Linux distros, but I can't until my hard drive is properly partitioned.  So what do I need to safely partition this hard drive so I can move on with my life (preferably with alternatives to the external hard drive.

110 gigs of data need to be backed up, minus the size of Windows.  This also does not include anything that I do not want and also don't need.

To partition your drive, you can safely use this: [http://partedmagic.com/](http://partedmagic.com/)
I've used it on Windows partitions AFTER I defragged the hard drive. This is important. I hosed a Windows installation because I didn't defrag first. Learn from my mistake.

---

### Post by Dullstar on 2009-09-27
Defragmentation is in process, and I'm going to backup the data I'd miss the most if I lost it onto my flash drive.

---

### Post by Dullstar on 2009-09-27
Another question.  I rebooted into Windows earlier to play a game that doesn't work in WINE.  Am I going to need to boot back into Ubuntu to use this?

Yes or no answers will do here.

EDIT:  I don't know if these will seem obvious, but the reason I have Ubuntu installed, but not given a partition is because I installed using Wubi.  I seem to recall getting a link to a tool to change the Wubi file to a real partition, though.  Man, I can't wait to try more Distros!  I'm going to have to download some .iso files!

---

### Post by oboedad55 on 2009-09-27
[QUOTE=Dullstar;8017530]Another question.  I rebooted into Windows earlier to play a game that doesn't work in WINE.  Am I going to need to boot back into Ubuntu to use this?

Maybe I'm kind of dense, but I don't understand the question. Boot back into Ubuntu to use what?

---

### Post by Dullstar on 2009-09-27
Parted Magic.

---

### Post by oboedad55 on 2009-09-27
> **Dullstar said:**
> Parted Magic.

Parted Magic is a stand-alone partition editor. GParted comes along with Ubuntu, so in the second case, yes. In the frist you burn a CD and boot from that CD.

---

### Post by Dullstar on 2009-09-27
So, I just download that?  Or, should I just reboot and use GParted?

---

### Post by jmwink on 2009-09-27
Seems like its up to you. If it were me, I'd download the Parted Magic OS and use the Boot CD.

---

### Post by Dullstar on 2009-09-27
Okay, so you guys are sure it will be safe to do this?

---

### Post by alms66 on 2009-09-27
There are no guarantees with partitioning.

I would highly recommend backing up all your important data on cd or dvd before going through with this.  I've yet to actually have resizing a partition work for me without messing something up.  With that said, I've only done it a few times and I've never used Parted Magic either.

---

### Post by oboedad55 on 2009-09-27
> **Dullstar said:**
> Okay, so you guys are sure it will be safe to do this?

If you've followed the suggestions you should be fine. Nothing is perfect, however, which is why you backed up your data. You did back up your data, didn't you?

---

### Post by darkstaar on 2009-09-27
There's always some risk when modifying partitions on a hard drive. However, in my experience, the biggest danger by far comes from human error.

Try to refrain from drinking too many beers before performing this operation and you'll be fine.

---

### Post by oboedad55 on 2009-09-27
> **darkstaar said:**
> There's always some risk when modifying partitions on a hard drive. However, in my experience, the biggest danger by far comes from human error.

Try to refrain from drinking too many beers before performing this operation and you'll be fine.

Good idea! Not too much beer. Just enough. My experience has been the same in that the screw-ups have come on my end, whether it was not defragging a Windows drive or whatever. I have yet (knock on wood) to have things just mess themselves up. And if the OP is scrupulous then he/she will be fine too and all will be right with the world.

---

### Post by Dullstar on 2009-09-28
Thanks, I'll get to doing this once I get home from school.
By posting this, I'm risking being late.

---

### Post by t0p on 2009-09-28
Please remember: before you start messing with the partitions on your hard drive, **BACK UP ALL THE DATA THAT YOU DON'T WANT TO LOSE!!!**.  Parted Magic and GParted are pretty safe tools to use, but **nothing is guaranteed**!

Oh yeah, in answer to a previous question:  Parted Magic comes on its own bootable disk, so you can use that to partition your hard drive.  But you can't use GParted from your Ubuntu installation to do it.  Your hard drive must be unmounted in order to partition it.

So you can use Parted Magic from its own bootable disk, or you can use GParted from your Ubuntu live cd.  But not GParted from your installed Ubuntu.

---

### Post by Dullstar on 2009-09-28
OK, maybe I won't get to it today, but I will start backing things up.

---

### Post by Dullstar on 2009-09-28
> **oboedad55 said:**
> If you've followed the suggestions you should be fine. Nothing is perfect, however, which is why you backed up your data. You did back up your data, didn't you?

I guess I'll be backing up my MVG (most valuable gigabytes)!

---

### Post by Dullstar on 2009-09-28
Compressing data so it fits on my flash drive. :)
Currently waiting for my most important folder, "Infinity" to compress.

I could place some of it on the old computers in the basement.  There's got to be enough hard disk space to get some of it.  OR maybe all of it, I don't know.

---

### Post by Dullstar on 2009-10-11
Too bad I can't find too much space for backups.  Oh well.

---

