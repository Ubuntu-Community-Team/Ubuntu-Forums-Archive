---
title: "How to uninstall Windows 7 within 11.04"
date: 2011-07-01
forum: General Help
---

### Post by MotherMonster on 2011-07-01
Hi, I've been using Ubuntu for atleast 8 months now but today I bought a new laptop and I followed a thread that said to install gpartition and delete all the partitions that said "FAT32" and "nfts" or something but all but one had those and it was called "unallocated" with no memory. It was easier on 10.10 because it asked if I wanted to fully erase Windows. How do I do this safely and JUST KEEP UBUNTU 11.04 on my laptop?

ThankyoU!

---

### Post by ajgreeny on 2011-07-01
If you really want to get rid of everything on the computer at the moment, and have just ubuntu with no windows, you can simply choose the whole disk at the time of installation of ubuntu.

It is also worth following the information on [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") as it will make life a lot easier when you need to re-install your OS, or do a clean install upgrade of the distro. You will need to choose "Something else" at the Prepare disks stage of install to get you to the manual partitioning, where you can delete all the current partitions if that is what you really want.

If you already have ubuntu installed, run gparted and copy a screenshot of that back here.  It will make it much easier to tell you what to do next.

---

### Post by Mark Phelps on 2011-07-01
You said > and JUST KEEP UBUNTU 11.04 on my laptop meaning, it's already installed, right?

If ALL your partitions are NTFS, then you can NOT remove Win7 and KEEP Ubuntu because you installed it via Wubi, meaning it's contained within a file on one of the NTFS partitions.

If you installed this way and already erased the NTFS partitions, then Ubuntu is already gone.

---

