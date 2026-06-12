---
title: "Triple-booting with 6 partitions"
date: 2011-09-14
forum: General Help
---

### Post by Auslegung on 2011-09-14
I currently have a dual-boot setup, Win7/10.04, but will soon need a triple-boot setup, Win7/10.04/OSX.  My current dual-boot setup is Win7, unallocated space, Ubuntu root, swap, and Home.  

Is there any way to shrink my Home partition, combine the two unallocated spaces into one (they would not be adjacent), and make from them a partition (NTFS or FAT32, which would be better?) that all my OSs can share, and an OSX partition, [COLOR="Red"]without losing data[/COLOR]?  What would be the easiest way?  

I'm thinking erase the swap first, then make an extended partition that will encompass my Root, Home, and Swap, then use the rest to make the partition that will be shared and the OSX partition.  That would look like this: Win7, Extended partition (Root, Swap, Home), Shared Data Partition, OSX.  I've heard that any extended partition must be first on the disk, is that correct?  No matter what I do it's going to take quite a long time, isn't it?

Also, I have a 500GB external hard drive that is NTFS but I want to make a liveCD on it.  Yesterday I tried for several hours to make both a 4GB NTFS and FAT32 partition on it, put the LiveCD on either one, and boot, but I guess my BIOS didn't recognize the other partitions or something, and I could never get it to work.  I eventually took my microSD from my phone and put the LiveCD on it without losing any data.  I now have only one partition on my external hard drive, still NTFS.  Can I put a LiveCD on the one partition without losing data?  Will it work being NTFS, or must it be formatted to FAT32?

Slightly off-topic.  What cool things could I do with partitioning this external hard drive?  The best I could come up with was several different LiveCDs, but I guess my BIOS won't allow that.

Thanks for your help.

---

### Post by ubiquitin.jf on 2011-09-14
You *can* do that from something like the Gparted live CD but it will take absolutely ages.

---

### Post by Auslegung on 2011-09-14
> **ubiquitin.jf said:**
> You *can* do that from something like the Gparted live CD but it will take absolutely ages.

Yeah I know...

I'm beginning to think I should just make an .iso of my current Ubuntu setup, delete all my linux partitions leaving only my Win7 partition, and start all over.  Would that just be simpler and cleaner, and maybe even a little faster?

---

### Post by Mark Phelps on 2011-09-14
> **Auslegung said:**
> I currently have a dual-boot setup, Win7/10.04, but will soon need a triple-boot setup, Win7/10.04/OSX.  My current dual-boot setup is Win7, unallocated space, Ubuntu root, swap, and Home.  

Is there any way to shrink my Home partition, combine the two unallocated spaces into one (they would not be adjacent)
NO -- can only combine adjacent spaces.
> , and make from them a partition (NTFS or FAT32, which would be better?)that all my OSs can share, and an OSX partition, [COLOR="Red"]without losing data[/COLOR]?  What would be the easiest way? 
Sorry, don't use OSX.  If you want to share only between Windows and Linux, NTFS would be the better choice.  But, don't know if Macs can read/write NTFS. 

> I've heard that any extended partition must be first on the disk, is that correct?  Most definitely NOT true.  Extended partition can be anywhere in the sequence on a drive.
>  No matter what I do it's going to take quite a long time, isn't it?  Using GParted (which I'm guessing you will do), then YES ... this is going to take a LONG time.
> Also, I have a 500GB external hard drive that is NTFS but I want to make a liveCD on it. ... Will it work being NTFS, or must it be formatted to FAT32?
My guess is that your SD card was formatted to FAT -- not NTFS.  I've used SD cards as large as 16GB, and even then, they were not preformatted to NTFS.  I don't believe that you can put LiveCDs on NTFS partitions.

> Slightly off-topic.  What cool things could I do with partitioning this external hard drive?  The best I could come up with was several different LiveCDs, but I guess my BIOS won't allow that.
If you mean, using your BIOS to select from among different OSs on the same external drive, I don't believe you can do that.

---

### Post by Auslegung on 2011-09-14
> **Mark Phelps said:**
> NO -- can only combine adjacent spaces.  First, thanks for addressing all my questions.  I'm aware that one can only combine adjacent spaces; that's part of my question.  The moving of those non-adjacent spaces is going to take time, and will it necessarily cause any loss of data?


> **Mark Phelps said:**
> Extended partition can be anywhere in the sequence on a drive. Thank you, that helps.

> **Mark Phelps said:**
> My guess is that your SD card was formatted to FAT -- not NTFS. [...]  I don't believe that you can put LiveCDs on NTFS partitions.  Yes, my sd was FAT32.  That's why I'm asking if that was the issue, FAT32 vs NTFS, or was it because I was using an external hard drive with multiple partitions.

---

### Post by srs5694 on 2011-09-14
> **Auslegung said:**
> I'm aware that one can only combine adjacent spaces; that's part of my question.  The moving of those non-adjacent spaces is going to take time, and will it necessarily cause any loss of data?

You don't really move unallocated spaces; you move the allocated partitions that exist *between* the unallocated spaces. When you do so, you can end up with a single bigger unallocated space when you used to have two or more smaller unallocated spaces. GParted and various other utilities can do this, but as you say, it takes time. More importantly, it's risky -- a power loss, cat yanking out a cable, system crash, bug, or other problem can lead to data loss. Always back up your important data before trying something like this.

It sounds like a better solution in your case may be to add a new physical hard disk. That can minimize the amount of mucking about you need to do on your current disk. Having two physical disks can also minimize the boot loader risks associated with installing a new OS -- you can physically unplug your current disk, install a new OS to the new disk, test it, reconnect the old disk, and then tweak your boot loader configuration so that they all work. With just one disk, when the new OS installs it's boot loader, you're as likely to end up losing the ability to boot one or more of your current OSes as you are to have everything work, and getting it all back can be a daunting task. Installing a new OS to a new disk will usually give you the option of booting any OS by adjusting BIOS boot-time options, at least as a temporary workaround while you work out the boot loader issues. There are also issues of partition table type (MBR vs. GPT) for OS X and Windows on one computer, but as running OS X on standard PCs (if that's what you intend) is verboten here, I won't say more about that topic. (If you've got a Mac but don't currently run OS X, that's another matter, and a triple-boot setup can be discussed in more detail.)

---

### Post by Auslegung on 2011-09-16
> **srs5694 said:**
> You don't really move unallocated spaces

I'm aware of this, it's splitting hairs and the equivalent of calling someone out for saying the sun rises and sets, when in reality the earth is the one doing all the moving.

> **srs5694 said:**
> It sounds like a better solution in your case may be to add a new physical hard disk. 

Maybe running win7 from an external hard drive is a possibility, thanks for the idea and I'll look that up.  However, I have an older laptop and don't want to put any money into it; I don't want to change out my internal hard drive, nor can I add one.  And yes I own win7 and OSX legitimately.

I'm beginning to think the easiest of all possible solutions is to buy a Mac, and start all over from there.

---

### Post by srs5694 on 2011-09-16
> **Auslegung said:**
> [quote=srs5694]You don't really move unallocated spacesI'm aware of this, it's splitting hairs and the equivalent of calling someone out for saying the sun rises and sets, when in reality the earth is the one doing all the moving.[/quote]

 My apologies if I offended you; that certainly wasn't my intent. Many people *are* confused about this point, and it can be important. For instance, in dealing with the 4-primary-partition limit of MBR disks, people are sometimes confused by the fact that they can't create a partition "when one clearly exists" (referring to an unpartitioned space). There are also issues about free space in vs. out of an extended partition. All of this makes more sense when you think in terms of moving partitions rather than free space.

> Maybe running win7 from an external hard drive is a possibility, thanks for the idea and I'll look that up.  However, I have an older laptop and don't want to put any money into it; I don't want to change out my internal hard drive, nor can I add one.Running on a laptop does limit your options. I seem to vaguely recall that Windows won't install to an external drive, but I'm far from positive of that. Since the OS you want to add is OS X and since discussion of it is verboten here, I don't feel I should comment on its ability to run from an external drive, but you could ask about that on a Hackintosh site.

> And yes I own win7 and OSX legitimately.That's irrelevant to the forum rules, which the moderators interpret as forbidding discussion of running OS X on non-Apple hardware, since doing so violates the EULA for OS X.

> I'm beginning to think the easiest of all possible solutions is to buy a Mac, and start all over from there.Probably. In addition to being a verboten topic here, running OS X on PC hardware is challenging and can be very frustrating. It can work reasonably well if you happen to have *exactly* the right hardware and/or if you have a guide that describes how to do it on your exact hardware. The trouble is that OS X was designed for Apple's specific hardware, and the further your hardware deviates from Apple's, the harder it is to get drivers and other software components to work. Even different firmware on otherwise similar video cards can pose problems.

Be aware, though, that triple-booting real Macs can be challenging, too. You run into issues with [hybrid MBR partition tables,]("http://www.rodsbooks.com/gdisk/hybrid.html") boot loader configuration, EFI vs. BIOS boot modes, etc. IMHO, the best way to run OS X, Linux, and Windows on a Mac is to run Windows in a virtual machine (VirtualBox, VMware, etc.), and perhaps Linux, too. That can simplify the partitioning and boot loader configuration quite a bit and make it less dangerous in the long run.

---

### Post by Auslegung on 2011-09-16
> **srs5694 said:**
>  My apologies if I offended you; that certainly wasn't my intent 

You didn't offend me, though I can see how my response looks snarky and rude.  I'm sorry for that.  I think I'll hold off on triple booting (though I really want to do it just to do it, at this point) until I get a mak, and likely run windoze in boot camp or whatever virtual box they have.  Thanks for replying, and helping me think about this.

---

### Post by srs5694 on 2011-09-16
> **Auslegung said:**
> You didn't offend me, though I can see how my response looks snarky and rude.  I'm sorry for that.

No problem.

> I think I'll hold off on triple booting (though I really want to do it just to do it, at this point) until I get a mak, and likely run windoze in boot camp or whatever virtual box they have.  Thanks for replying, and helping me think about this.

[VirtualBox](http://www.virtualbox.org/) is available for Mac, as are several others. I use VirtualBox myself on my main Linux system and it does a very good job of handling Linux, FreeBSD, OS/2, and Windows, at least. It might not be adequate for gaming or if you need direct low-level access to the hardware (for using specialized PCI cards or something), but for running many programs, it's quite adequate.

Boot Camp is popular and useful if you need a true dual-boot setup; however, my opinion of [hybrid MBRs,](http://www.rodsbooks.com/gdisk/hybrid.html) upon which it relies, is quite low. When I first heard about them they seemed like a clever hack, but the number of problems they create (both theoretical and in real life) is astonishing. I realize that some people do need true dual-boot Windows/OS X systems, so I can't recommend that a Mac *never* be configured in this way; but IMHO it should be considered a configuration of last resort. If you must do it, you should take several preventive measures:


[list]
[*]Read up on the topic. To the best of my knowledge, my own [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) page is the only site that provides much in the way of details about hybrid MBRs. If you know of another site, I'd love to hear about it.
[*]Back up your partition table, including both GPT and MBR information. My [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program can do this in one go, but you can use dd and/or sfdisk to back up some or all of the data in other ways. Cutting-and-pasting text displays from parted, fdisk, gdisk, or other tools can also be useful, but be sure the display you've got shows partition start and end points to the sector. (fdisk defaults to cylinder displays, and parted usually rounds to mebibytes, gibibytes, or tebibytes.) If something goes badly wrong, a backup may be your only way to recover.
[*]With few exceptions, you should use GPT disk utilities to modify the partition table and then (if necessary) create a fresh new hybrid MBR after changing things on the GPT side. In an OS X/Windows dual-boot setup, this means doing the work from OS X, *not* from Windows. I've seen posts from people who've trashed their disks by repartitioning a hybrid MBR disk from Windows. I seem to recall once where recovery was possible, but more often they end up repartitioning from scratch and re-installing/restoring data.
[*]Keep backups of your regular data. This is advisable for *any* disk, but the extra risks of a hybrid MBR make it even more important for such disks.
[/list]


Adding a third OS, such as Linux, to a hybrid MBR increases the complexity. It's do-able, and it's not even much harder from a partitioning perspective if you know what you're doing. If you *don't* know what you're doing, though, it's a big gamble; it may work great the first time or you may end up pulling a lot of hair out trying to figure out why it doesn't work.

An OS X/Linux dual-boot on a Mac is both easier and more difficult than an OS X/Windows dual boot. It's possible to configure Linux to boot in EFI mode, which obviates the need for a hybrid MBR and all its problems; but most installation procedures you read about rely on Boot Camp to get things started. Ubuntu's EFI-mode installer is still problematic. (I hope it'll improve in 11.10, but I haven't checked the latest beta.)

---

