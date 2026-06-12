---
title: "Are two swap partitions needed?"
date: 2011-11-11
forum: General Help
---

### Post by JonUK76 on 2011-11-11
I've noticed that there are two swap partitions in Ubuntu.  I was just wondering why that was, is it normal, and if both are not needed is it possible to "reclaim" the space from one of them?  I.e. ideally I'd like to merge one of them with sda6.

My setup is Windows 7/Ubuntu dual boot.  I recently had to do a "clean" installation of Ubuntu 11.10 due to a failed upgrade from 11.04.  I just chose the "delete existing Ubuntu 11.10 and install Ubuntu 11.10" option in the installer without manually specifying partition info.

The output from fdisk -ls is:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x94d509e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1910546189   955169671    7  HPFS/NTFS/exFAT
/dev/sda3      1910546430  1953520064    21486817+   5  Extended
/dev/sda5      1951640523  1953520064      939771   82  Linux swap / Solaris
/dev/sda6      1910546432  1943269375    16361472   83  Linux
/dev/sda7      1943271424  1951639551     4184064   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Thanks for any advice.

---

### Post by scradock on 2011-11-11
There is certainly no need for two swap partitions. You should be able to merge sda7 with sda6 with minimal fuss using gparted - make sure you set sda7 to inactive "swapoff" first, and have sda5 active.

You may be able to delete sda7 while running Ubuntu in sda6, but probably won't be able to grow sda6 into the empty space. For that you should boot from the install liveCD, and run gparted from there. You'll have to unmount sda6, which is why you can't do it while running from sda6.

---

### Post by 1clue on 2011-11-11
The answer to your question depends on information we don't have.

I use 4 swap partitions, one on each non-removable disk.  I'm doing some special optimization though.

So answer these questions:
[LIST=1]
[*]How much RAM do you have?
[*]How long does your system stay up, in days, on average?
[*]What does your memory usage look like right before you shutdown/reboot?
[*]Do you ever run out of memory?
[*]Do you use tmpfs?  If so, what partitions use it?
[/LIST]

I use a lot of tmpfs filesystems because I am a software developer, and I put the build products in tmpfs partitions because it's writing straight to RAM, and it speeds things up a lot.  If you do this sort of thing, then a larger SWAP partition makes sense because that's where the "reserve space" for tmpfs goes.

If you just used the GUI installer and left your system like that, then you don't use tmpfs much.  In that case you don't need a lot of room there.  Last I heard the normal rule of thumb was 1.5 times the amount of RAM you have, but today many systems have enough RAM that they never hit SWAP and they don't necessarily tune anything for performance, so SWAP isn't really even necessary at all in some modern systems.

---

### Post by wojox on 2011-11-11
Yopu just need to figure out which one your using and remove the other with a live-cd and gparted.

---

### Post by JonUK76 on 2011-11-12
Thanks for responses :)

I've found that the 4gb swap partition (sda7) is active and the 1gb one (sda5) is inactive.  The RAM is 4gb and I don't do any development, as you've probably guessed!  System might be up for a couple of days at most.   Probably the most strain it would be under would be running a few desktop apps and VMWare, or maybe some video encoding using Handbrake. Nothing too specialised.  TBH I don't often see physical memory usage go over 40% or so, but it does use some swap space at times regardless (not a huge amount).  I assume the reason they set it to default at 4gb is to allow for hibernation?

I've been having a read of the guide on swap here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) which is quite good. Not sure what to do though.

---

### Post by 1clue on 2011-11-12
How big is the VM?  How many VMs?  That can make a lot of difference and is pretty much the reason why I have 12G.  Multiple VMs and a couple of them are large.

If you want to hibernate you need SWAP to be as big as RAM.  If you're either on or off, you don't need swap at all.

---

### Post by JonUK76 on 2011-11-12
Generally a VM (WinXP) with 1Gb memory allocated which I use frequently, but have a few others I use occasionally (e.g. FreeBSD, other distro's) which are about the same size.  I wouldn't say I've ever really needed to use multiple VM's so far though.

---

### Post by 1clue on 2011-11-12
> **JonUK76 said:**
> Generally a VM (WinXP) with 1Gb memory allocated which I use frequently, but have a few others I use occasionally (e.g. FreeBSD, other distro's) which are about the same size.  I wouldn't say I've ever really needed to use multiple VM's so far though.

OK you're still probably good with 4G.

FWIW if your box supports it I can't remember when memory was cheaper.  I've even contemplated switching to 4G sticks on my system, even though right at the moment I can't imagine needing more than the 12G I have.  I've never used more than 11.  We recently doubled our laptop memory at work, ddr3 laptop memory we got 2x4G sticks for $90 a pair.  If your box is a desktop then you're certain to be able to do the same for cheaper.

---

### Post by JonUK76 on 2011-11-12
Thanks.  Yes you're right, I can't believe how cheap RAM is at the moment.  8gb DDR3 is about half the price I paid for 4Gb at start of 2010.  And RAM prices are cyclical so best to buy when it's cheap :)

---

