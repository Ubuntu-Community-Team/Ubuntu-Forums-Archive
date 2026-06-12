---
title: "duel booting 7 and ubuntu?"
date: 2010-04-17
forum: General Help
---

### Post by Jonty789 on 2010-04-17
hello everyone!

Is it possible to duel boot Window 7 and Ubuntu?

I just want to make sure it fine before i do it

thanks :)

---

### Post by Eraemaajaervi on 2010-04-17
it's no problem. just install Ubuntu after Windows 7 and make sure Ubuntu gets it own partition.
If you don't assign any mount point to the Windows parition, Ubuntu won't touch it. In fact, grub will ask you on boot, which system you want to start.

---

### Post by oldfred on 2010-04-17
several versions
Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

If any of the instruction refer to grub and not to grub2 besure to see the updates for reinstalling grub2 if you install windows after Ubuntu.

Generally if you have win7 installed it is better to use win7 tools to shrink the win7 partition and reboot win7 several times to make sure it has reset to its newer smaller size. It will usually want to run chkdsk and maybe other repairs on a resize. Then install Ubuntu in the free space you made.

---

### Post by oracle2b on 2010-04-17
yes ubuntu is able to dual boot with windows 7. I'd recommend installing ubuntu on a seperate partition. 
1. Defrag your windows hard drive

2. shrink your partition to a your desired size from windows computer management in adminstrative tools.

3. reboot to ensure everything works well.

4. boot with ubuntu cd/dvd or usb and install, brub will handle the dual boot and you're done.

---

### Post by Cubhicbu on 2010-04-17
There are several ways to do this. One of the easiest is to first install Windows 7, then use the Wubi installer on the disk to install it inside Windows. 

Or, you can start up from the Ubuntu disk (I'd recommend first installing Windows 7, or it might remove Ubuntu) and give it a partition next to Windows.

---

### Post by hawthornso23 on 2010-04-17
Duel booting ... where the operating systems fight over the hardware?

---

### Post by Vined Adobo on 2010-04-25
> **oldfred said:**
> several versions
Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

If any of the instruction refer to grub and not to grub2 besure to see the updates for reinstalling grub2 if you install windows after Ubuntu.

Generally if you have win7 installed it is better to use win7 tools to shrink the win7 partition and reboot win7 several times to make sure it has reset to its newer smaller size. It will usually want to run chkdsk and maybe other repairs on a resize. Then install Ubuntu in the free space you made.


I agree you should shrink with Windows if you can, but when, in anticipation of Lucid release, my wife requested that I get her netbook, which she got for Christmas, ready.  I tried to use windows 7 to shrink the partition, but it complained that there was no room after the last w 7 file to make any new partition at all.  W 7 had put a paging file or something at the very end of the partition and since windows was running,  I couldn't do anything with it.

To fix the problem, I put ubuntu live on a memory stick (netbooks don't have cd drives) and booted into "try ubuntu before installing."  Went to system > administration > gparted and shrank the w 7 partition from there.  Worked fine.  W 7 came back after reboot and fixed itself to accommodate smaller partition and w 7 works fine (at least as well as w 7 *can* work.)


Remember everyone: Backup Backup Backup! Read and understand what you want to do and then don't do anything at all unless you're willing to recover from some mistake you might make.

Dave

---

### Post by Zintha on 2010-04-25
Sorry to use someone elses topic, but would it be easier to have a second HDD and just install to there?

Skips all the partitioning.

---

### Post by wilee-nilee on 2010-04-25
> **Zintha said:**
> Sorry to use someone elses topic, but would it be easier to have a second HDD and just install to there?

Skips all the partitioning.

Not necessarily, there are variables involved. A second hard drive would be a good place to back stuff up and or have the home partition, and other variables. Partitioning is easy once you know how.

---

