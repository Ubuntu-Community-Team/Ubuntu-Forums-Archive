---
title: "Doing a clean reinstall+ re-partitioning my system"
date: 2011-03-13
forum: General Help
---

### Post by ULAMSS5 on 2011-03-13
Hi everyone, I am currently using windows 7+ubuntu 10.10 with grub, with the hard drive(120GB) partitioned like this

|C:/ 40GB | D:/ 60GB | Ubuntu: 20GB|

Due to unfathomable reasons, the driver guys/dell refuse to provide drivers for my computer in windows 7, and it's really affecting me in many ways. Using vista drivers are buggy, too.

I want to do a clean re-install of my system, turning it into a Vista(without ubuntu), which is "supported" on my computer, while changing the partitions to

|C:/ 30GB | D:/ 90GB|

As this will be the first time I re-format the computer by myself, I would like to take some precautions and clarify some doubts.
1: How will I be able to cleanly reformat my system, getting rid of both 7 and ubuntu, plus everything else? Is it simply clicking on a clean full/partial format option kind of thing? or are there extra steps to un-install ubuntu first?
2: Will the Partitioning be able to be done while in my re-formatting, is it part of the process? or do i need to get extra programs or steps to do the re-partitioning?

Thanks in advance for all helpful responses :)

---

### Post by kn0w-b1nary on 2011-03-13
You don't have to unistall ubuntu. You run a partitioner like GParted, and you can use that tool to both repartition and reformat the disk. just reformat the entire drive and everything will be gone.

---

### Post by akand074 on 2011-03-13
I'm pretty sure the Windows disk can do this, but if not then yes just boot into an Ubuntu LiveCD and open Gparted and delete every partition so that you only have unallocated space. You can then either format it to NTFS or just let the Windows disk do it. Just pop in the disk and install Windows afterwards (using the whole disk). Once you are in Windows you could easily shrink it and make your other partition.

---

### Post by wilee-nilee on 2011-03-13
Yeah gparted is a good tool, lets get a screenshot of it, just boot the Ubuntu live cd and take a pic and post it. There is probably other partitions on there I would bet money that there are 4 primaries already the max allowed. Not a big deal though it is just a matter of knowing what's up.

---

### Post by ULAMSS5 on 2011-03-14
Wow guys thanks for the really fast replies! I'm downloading Gparted now, I'll get to the repartitioning and reformating once i get my hands on another external hard drive to back up my stuff. I guess this can be considered solved.
Once again, thanks!

---

### Post by wilee-nilee on 2011-03-14
> **ULAMSS5 said:**
> Wow guys thanks for the really fast replies! I'm downloading Gparted now, I'll get to the repartitioning and reformating once i get my hands on another external hard drive to back up my stuff. I guess this can be considered solved.
Once again, thanks!

Yeah for resizing the W7 use its disk manager, as post 3 suggests. Make sure you don't already have 4 primary partitions already if so that is the limit.

---

