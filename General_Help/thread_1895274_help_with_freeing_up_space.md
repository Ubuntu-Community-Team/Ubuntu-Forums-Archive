---
title: "help with freeing up space?"
date: 2011-12-14
forum: General Help
---

### Post by mwentz on 2011-12-14
Hello all, I am currently running a dual-boot with Ubuntu 11.10 and Windows 7.  As much as I love Ubuntu, there are unfortunately some needs for me that require Windows :mad:.  That being said I have a pretty fresh install and dedicated about 50 gigs to my Ubuntu partition and approximately 45 for Windows.  Here is the problem, I am running out of space on the Windows partition with just the bare necessitates installed.  Is there any way to add space from the Ubuntu partition without totally screwing everything up? I have my Ubuntu just the way I want it so I dont want to have to reinstall anything /if possible/...

Any help would be appreciated...

P.S. as my first post I want to say a quick hi and go easy if i happened to mispost, I also googled the SH** outta this and am familiar with ubuntu and how to figure out things on my own however no help for my specific problem. Thanks again.

---

### Post by seawolf167 on 2011-12-14
You can resize your Ubuntu partition with [GParted]("https://help.ubuntu.com/community/GParted") (should be installed by default, hit [ALT][F2] then type in "gparted" to open the program) to free up space, then assuming you are using Windows 7 you can resize your Windows 7 partition into the newly created free space by right-clicking "My Computer", selecting "Manage", then selecting "Disk Management" and resizing the C: volume.

It is always suggested (and a good idea) to backup before you begin in case something happens. I suggest using [Clonezilla ]("http://www.clonezilla.org")to create an image of your entire drive just incase something goes wrong.

---

