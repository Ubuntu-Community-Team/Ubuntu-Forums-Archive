---
title: "Data Recovery"
date: 2009-11-25
forum: General Help
---

### Post by my2009ch on 2009-11-25
Later today i messed up my WinXp computer when i decided i no longer wanted to have the beta version of win7 on my computer. So i deleted the partition and ran fixmbr and fixboot in the windows xp recovery console. Bad idea, now i can not load xp, i get the following error: A disk read error occurred, Press Ctrl+Alt+Del to restart. So, in an attempt to recover the data on the drive, it installed the drive into a computer i have that runs ubuntu. When in ubuntu, the drive does not show up under Places > Computer. But, if i go to System > Administration > Disk Utility, The drive is shown as:
500GB Hard Drive
>ATA ST3500630AS
>MBR Partition Table

>>500 GB Unrecognized
>>Unknown or Unused

Is there any why to get the data off the disc or did i wipe it all out?

---

### Post by audiomick on 2009-11-25
Hallo.
I'm not that up on this, but:
If you run gparted, it should show you what partitions are on the drive, and where the computer has registered them, and what file system is on them.

The drive is not in places because it is not mounted.

When you know where it is, you should be able to mount it and get the files of, as long as you haven't shot it down.

I'm sorry, but I am too unsure of the use of the mount command to try and tell you how to use it. 

I hope someone else has some more advice for you.

---

### Post by rbc on 2009-11-25
A partition is what is shown in Places, not a drive, although in many cases a partition takes up the whole drive. And it doesn’t have to be mounted to show up there. Ubuntu is seeing the hard drive but, I believe, does not recognize a valid partition, so it doesn’t know how to mount it. I suggest downloading Testdisk from the repos, and see if it can reconstruct the partition

---

### Post by my2009ch on 2009-11-25
IN GParted i get a warning for the drive that i would like to get the data off of, the warning reads: Unable to read the contents of this file system!, Because of this some operations may be unavailable"

---

### Post by audiomick on 2009-11-25
> **my2009ch said:**
> IN GParted i get a warning for the drive that i would like to get the data off of, the warning reads: Unable to read the contents of this file system!, Because of this some operations may be unavailable"

Don't like the sound of that. Better try what rbc suggested...

---

