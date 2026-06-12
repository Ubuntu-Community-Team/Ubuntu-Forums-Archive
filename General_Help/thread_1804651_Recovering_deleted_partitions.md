---
title: "Recovering deleted partitions"
date: 2011-07-15
forum: General Help
---

### Post by Jagoly on 2011-07-15
Alright, so at the moment I'm feeling very stupid. I was intending to install ubuntu 11.04 to eventually replace my xubuntu installation. To do this, I started by booting into windows 7 (laptop is triple booted with xubuntu win7 and arch) to shrink my windows partiton. At this point, I realised that I probably would have to remove arch to make room for an extra os. I thought that my disks were aet up as:

windows
-   SYSTEM
-   WIN7
Extended1
-   Arch_Root
   Arch_Home
Extended2
-   Xubuntu
-   Swap
HPRECOVERY

Turns out that they were:

windows
-   SYSTEM
-   WIN7
Extended1
-   Arch_Root
-   Arch_Home
-   Xubuntu
Swap

And the windows partitioner decided to, because it doesn't give any usefull info on extended partitions, without telling me, when I chose to delete arch_root delete Arch_root, Arch_Home and Xubuntu.

Xubuntu has alot of important stuff I need back. Like I said, I was already intending to switch back to regular ubuntu (I'm sick of xubuntu lack of prettyness, and have begun to like unity) but I desperately need to recover the files on my xubuntu partition. Nothing has been written over the free space yet, so testdisk should work from a live cd to recover most files? or something better? can't test disk recover entire partition tables?

I could probably work it out myself, but all of my stuff is on there, so I'd like to get some advice from someone more experienced first.

---

### Post by Jagoly on 2011-07-15
Ok, so I ran the windows version of testdisk and they sort of fixed my hard disks.nt 

sort of. After quiting testdisk, I pressed "rescan disks" in the windows partitioner. That made windows BSOD. After rebooting, the grub happily showed up and I'm now happily running xubuntu. But now my disks look like this (see attatchment).

The ubuntu 10.10 partiton was deleted long ago, and attempting to mount it just spews out a bunch of errors. The arch home partiton was 16gb.

also, the hp tools partition is now shown as within the extended partiton. all of the partitions, when mounted, contain exactly what they used to (except ubuntu10.10). my guess is that testdisk just stuffed up something and that disk utility is not showing the true layout. also you can see that gparted just sees the whole disk as unallocated.

I'm not game to boot into windows at this point. I know that booting xubuntu is safe, so I'll use it to back up everything on all the partitions before doing anything else. I have made the HP recovery disks, so mabey I'll wipe the machine and reinstall everything. That way I get a clean install of windows aswell (bar the HP Crapware of course).

---

### Post by srs5694 on 2011-07-15
Chances are [FixParts](http://www.rodsbooks.com/fixparts/) will fix the problem. Read its documentation and post back if you have any questions.

---

