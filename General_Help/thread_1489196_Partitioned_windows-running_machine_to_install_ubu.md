---
title: "Partitioned windows-running machine to install ubuntu; would like reacess to windows"
date: 2010-05-20
forum: General Help
---

### Post by qoou on 2010-05-20
Brief, not that useful, summary:
I decided to get Ubuntu, could not use GParted to partition due to bad sectors. Found [this thread]("http://ubuntuforums.org/showthread.php?t=1244058"), followed it.

Detailed, step-by-step, description of what I did:
1. Decided to get Ubuntu.
2. Ran Ubuntu 10.04 (64-bit) off of my live CD.
3. Tried to partition Windows partition with GParted; GParted refused due to bad sectors, suggested using ntfsresize.
4. Found the thread linked to above.
5. My system was partitioned as follows, according to fdisk:
```
   Device              Start      End       Id      System
   /dev/sda1             1       37028      7       HPFS/NTFS
   /dev/sda2           37029     38913      7       HPFS/NTFS
```6. Ran ntfsresize -b -s 260000M /dev/sda1
7. Rebooted into Windows. Everything worked perfectly. My memory was, as expected, down to 250-something G.
8. Went back to running Ubuntu off of my live CD.
9. Decided to not risk partitioning on my own until I could back things up.
9. Ran ntfsresize -b /dev/sda1
10. Decided I didn't need to back things up.
11. Ran ntfsresize -b -s 260000M /dev/sda1.
12. Ran fdisk /dev/sda
13. Deleted /dev/sda1 (ran d, then 1 when prompted).
14. Remade /dev/sda1, smaller of course (ran n, then p, then 1, then +261000M).
15. Made /dev/sda1 bootable again (ran a, then 1).
16. Saved and exited fdisk (ran w).
17. Rebooted.
18. Windows gave me an error message along the lines of "Could not find partition" or "Could not read partition."
19. Ignored error message.
20. Installed Ubuntu on the newly freed hard drive space.
21. Ran Ubuntu off the Live CD to get to GParted.
21. Panicked when I noticed that GParted did not recognize the file system of /dev/sda1.
22. Deleted the Ubuntu partition with GParted.
23. Used fdisk to remake /dev/sda1 to its original size.
24. Ran ntfsresize -b /dev/sda1 to resize it to its original size.
25. Rebooted. Windows obviously did not boot.
26. Sighed.
27. Ran Ubuntu off my live CD again.
28. Repeated 12-20.


The current problem:
My Windows partition is now: labeled as having unknown file system (and not being able to find a NTFS label) by everything except fdisk, which says it is NTFS. I would like to get at least one specific megabyte of data off of my Windows partition.

The reason I'm hoping for a solution:
I never messed with the actual data on my hard drive, except for the small space I partitioned for Ubuntu. The data, therefore, is all there; if I can just convince something to mount my partition as NTFS file format, and ignore errors, I see no reason why I wouldn't be able to access my data.

Possible causes:
 - I might not have done steps 9 and 11 (my memory is not working well: massive sleep deprivation). Doing step 9, but not 11, might have been bad.
 - My 64-bit arhitecture caused problems (rather unlikely).
 - ???

Conclusion:
While this problem is not all that related to Ubuntu itself, and it was caused by my own stupidity (not backing up for one), I'm not quite sure where else I could seek help. As mentioned earlier, only 1M of my hard drive is actually both important and not backed up, but I'd rather like to recover that 1M.

---

### Post by cariboo on 2010-05-21
You can use testdisk to repair your damaged partition table, it is in the repositories. It is a command line app, so it has to be run in a terminal. Once it starts up the instructions are pretty self evident.

---

### Post by qoou on 2010-05-21
Thanks. I've now backed up the disk with photorec and started running testdisk. However: testdisk seems to be taken a rather long time, and thanks to testdisk I am now almost certain that the problem is that I did not perform step 11 (I partitioned with fdisk without properly using ntfsresize first).
Since I had ntfsresized Windows down properly just moments before, and assuming that ntfsresizing Windows up doesn't actually force it to expand to fill all the new space, the only problem would be that my computer thinks the NTFS partition should be larger than it is. Is there a quicker (and safer) way to fix this problem, or is my assumption utterly wrong and I should just wait testdisk through?

Edit:
Nevermind; problem solved.

---

