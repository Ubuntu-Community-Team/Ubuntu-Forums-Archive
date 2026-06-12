---
title: "Lots of little files, advice?"
date: 2010-10-05
forum: General Help
---

### Post by greenfox1505 on 2010-10-05
I'm running a Minecraft game server (Java) right now on a Win7 computer.  I have written batch files that run every hour for back up (runs 7zip command line to archive old World folders) and to run a mapping program (written in Java).

My question is would it be a big deal to convert this server over to an Ubuntu server, and would I lose features?  I haven't tried to work with Ubuntu Command Line or Ubuntu Batch, so I'm not very familar with it, any advice?



A big problem I'm having in Windows is HDD IO speeds.

Minecraft's world folder is made of of 55,045 files in 4,161 folders, each file is between 2 and 8 kilobytes.  The problem? The size of the folder is about  150mb, but the size on the disk is 200mb+ because of the Allocation Unit Size (something I'd have to re-install to fix).  My back up batch 7zips the back up every time it runs, so that keeps my back ups pretty small.  But every back up still takes forever since it has to keep referencing back to the directory.  My question for this is there a formation system that handles this better than NTFS or FAT?  I've tried to solve this with a RAM drive, but I don't have a lot of RAM to work with, and Ubuntu should use less RAM than Win7 but that's moot if I can't get use-able RAM drive for it.

Advice? Ideas? Suggestions?

---

### Post by oldos2er on 2010-10-05
Maybe this will get you started: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

