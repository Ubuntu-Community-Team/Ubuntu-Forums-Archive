---
title: "Reparation and ignore bad sectors"
date: 2010-12-08
forum: General Help
---

### Post by Chunkscout on 2010-12-08
I'm running windows 7 and ubuntu on my laptop and recently windows started giving me a blue screen and won't start (I can't boot into safe mode, command prompt, or even off a windows 7 disk). After booting into ubuntu and running gparted I found the cause to be a bad sector on my hard drive.

What I want to do now (and actually what I had been planning on doing for awhile) is to remove my windows partition, give all the space to ubuntu and just run windows as a vm instead.

Is there a way to use gparted to repartition my hard drive, give all of the space to ubuntu but make sure that I ignore the bad sector? I know this isn't a great permanent but I need a temporary fix asap to get some work done before I get a new hard drive.

I've found some info on the subject but so far everything has involved booting into windows at some point in the process and currently thats not an option.

---

### Post by srs5694 on 2010-12-08
Replace the hard drive *now*. Modern hard drives have the ability to transparently hide bad sectors, replacing them with a set of sectors held in reserve for precisely this purpose. If you're seeing bad sectors in an OS, then it means that the drive has run out of its reserve bad sectors, and chances are good that the drive is failing in a very major way. You might luck out and be able to use it for another week or month or year, but it's also quite possible that you'll see increasing numbers of bad sectors popping up in the next few minutes or hours. IMHO, it's not worth the risk to try to eek out a few extra days or weeks use from the drive.

That said, the -c option to mke2fs will do a bad blocks check when you create a new ext2/3/4 filesystem, and the -c option to e2fsck will do the same for an existing filesystem; check these programs' man pages for details. This might be useful if you really have no choice but to keep using the drive.

---

