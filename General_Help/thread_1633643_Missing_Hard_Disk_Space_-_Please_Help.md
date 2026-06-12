---
title: "Missing Hard Disk Space - Please Help"
date: 2010-11-29
forum: General Help
---

### Post by AJKolenc on 2010-11-29
I've been using Ubuntu for a few months now, but I haven't seen anything like this before  (I've searched for my problem around the internet and can't seem to find anything).

I have a 320GB hard drive that has 4 partitions: 2 Windows 7 partitions, 1 for Ubuntu, and another as a shared storage partition (NTFS). I recently decided to reorganize my files onto the Storage partition, such that all of my important files were on there. It appeared to work, and everything was fine.

Then I booted into Windows 7, which apparently was hibernating (it said "Resuming Windows" upon selecting it). When I looked at my Storage partition, it had a few scattered folders with nothing in them, when I had over 50GB of files on it previously. Naturally I was a bit worried, so I booted back into Ubuntu. Almost all of the files were missing, except two random folders (which total to 65KB). 

When I look at the drive, however, it says 57GB of the drive are used (it says this both through gparted and properties window). I tried to reveal hidden folders, but there were none. Is it possible that my files survived? If so, how can I recover them? If not, how can I get that space back? I've looked and I can't find the answer.

Output from 'sudo fdisk -l'
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3837    30717278+   7  HPFS/NTFS
/dev/sda3           35090       38913    30716280   83  Linux
/dev/sda4            3838       29333   204796620    7  HPFS/NTFS

sda4 is the Storage partition. Thank you!

---

### Post by AJKolenc on 2010-11-29
Nevermind, Windows took the liberty of deleting every index of the files I was missing while it was "checking the disk." FML.

---

### Post by akand074 on 2010-11-29
That is something I would add to fmylife.com but I don't think many people would understand. I feel your pain. I once accidentally wiped my entire hard drive and all the partitions on it. Managed to fix it though using some software. If you have a backup (which you probably should have made) then everything is good. Otherwise you could try software like [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). I think I also used [The Ultimate boot CD]("http://www.ultimatebootcd.com/") but I think what ended up working for me in the end is just TestDisk. If your files aren't backed up and they are very important to you, you can give those software a try.

---

