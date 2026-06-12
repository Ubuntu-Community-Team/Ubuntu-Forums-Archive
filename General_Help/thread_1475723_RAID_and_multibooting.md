---
title: "RAID and multibooting"
date: 2010-05-07
forum: General Help
---

### Post by MARAUDER2003 on 2010-05-07
Hello,

I had some questions about RAID since this the first time doing this. I currently have a single old IDE hard drive from which a triple boot (Windows XP, Windows 7 and Ubuntu 9.10), yeah I still need XP for a class the uses an old program that apparently won't be developed any further. Anyway, I managed to get a couple of new SATA hard drives at a really good price so my plan is to continue to triple boot with 10.04, XP and win7 in RAID 0 (which leaves software RAID out and I don't have a controller card so that leaves hardware RAID out). My raid will be provided by the motherboard BIOS (I think this is called fakeRAID). My question is in what order do I install the OSs? Normally, I partition the drive and then install XP, Win7 and then Linux and let grub do the loading, but after reading grub2 horror stories, well I don't know how this is going to turn out. Do you guys have any pointers/suggestions about this before I get into big problems? From what I can tell, I need to look for a floppy drive to load the XP raid driver just for starters. Thanks for the help.

---

### Post by mb_webguy on 2010-05-07
If the mobo is doing the RAIDing, then by the time you get to the point of installing the OSes, all you'll see is one "drive" (or rather two, if you're also using the IDE drive) rather than the separate physical drives.  Using RAID 0, if you're using two 1TB drives, once you boot up, start to install the OS, and get to the bit about partitioning, all you'll see is 2TB of unallocated space.

(And I'm assuming you know that RAID 0 doesn't actually provide any redundancy, and that if one of the drives dies, you'll lose all data on both...)

---

