---
title: "Is there a defragmenter on linux?"
date: 2009-10-02
forum: General Help
---

### Post by Naater on 2009-10-02
hi ppls! I have a question that has bothered me for a while. Usually, on my old windows XP, when ever there was a space problem I would just right-click on ye olde My Computer and start that defragmenter and most of the time it worked very well. The quesstion is is that I want to know if there is a defrag on my linux 9.01.

---

### Post by blur xc on 2009-10-02
not really.  the EXT3 filesystem doesn't need defragging...  It's just that fragging cool (sorry for the lame pun)...

[http://www.google.com/#hl=en&source=hp&q=why+doesn%27t+linux+need+defragmenting&aq=f&aqi=g2&oq=&fp=2cca7b2e99206b9c](http://www.google.com/#hl=en&source=hp&q=why+doesn%27t+linux+need+defragmenting&aq=f&aqi=g2&oq=&fp=2cca7b2e99206b9c)

BM

---

### Post by Naater on 2009-10-03
oh thx and no prob. I was just curious :)

---

### Post by MaxIBoy on 2009-10-03
Actually, it can start to get fragmented if the partition usage gets near 90%, which is why you don't want to create a whole bunch of tiny partitions. 

The EXT4 filesystem is eventually going to have a defragger for exactly these situations, and you can upgrade to EXT4 from EXT3 without reformatting or deleting anything. (Although you get better performance boosts if you do reformat.)

---

### Post by wilee-nilee on 2009-10-03
Since my external hard drive is ntfs even when I have solely used Ubuntu to write to it, it had huge fragmentation, at least that what my legal XP side said, so it is probably good to monitor anything outside of the standard linux ext's group.

---

### Post by 3rdalbum on 2009-10-03
Defragmenting does not free up disk space, it just re-organises the way the files are stored on the disk. So, for your purposes, defragmenting is totally unnecessary.

---

### Post by dcstar on 2009-10-03
> **MaxIBoy said:**
> Actually, it can start to get fragmented if the partition usage gets near 90%, which is why you don't want to create a whole bunch of tiny partitions. 

The EXT4 filesystem is eventually going to have a defragger for exactly these situations, and you can upgrade to EXT4 from EXT3 without reformatting or deleting anything. (Although you get better performance boosts if you do reformat.)

Any FS that gets over 90% full is going to have problems that a defragmenter is only going to wallpaper over, so the real solution is proper disk space management.

It looks like adding a defragmenter is pandering to those brainwashed by too many years of using Windows that you need things like this to make up for fundamental weaknesses (the Linux does not have).

---

### Post by XCan on 2009-10-04
Well, what if your drive gets fragmented by low disk space and you decide to fix it? Imho, it is far better then for a user to be aware of the problem, delete some files, and run a defrag, rather than delete some files, empty the drive, and copy the files back.

---

