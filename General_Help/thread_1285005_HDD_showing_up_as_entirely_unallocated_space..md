---
title: "HDD showing up as entirely unallocated space."
date: 2009-10-07
forum: General Help
---

### Post by rafaelous on 2009-10-07
I've been having a problem with my HDD in my PC all along, only now I'm actually doing something about it. Basically Windows works fine (I'm dual booting Vista and 7) and I can mess around with my partitions in the partition editor whatever it's called in windows. However I now want to install linux so this is a major problem for me. I got out a Ubuntu 9 LiveCD, and opened GParted to make a new partition before installing it. Whe i opened GParted the HDD showed as unallocated space, the whole thing!

A guy was helping me out on an IRC channel earlier, but then he had to go so i was wondering if anyone here could help me with it? This is basically what I went through with him before and where I'm at now.

I opened terminal and typed:
```
sudo fsck /dev/sda
```
I got back from it this:
```
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:	e2fsck -b 8193 <device>
```

I'm not sure what that means or what to do now, so I would be grateful if anyone could help me with it.

---

### Post by alphaniner on 2009-10-07
**fsck** is file system check.  It is meant to be run on a partition (ie sda1, sda2, etc) with an ext filesystem.  The syntax you're using is trying to run it on the whole disk.  But since you only have Windows partitions, it wouldn't have worked even if you were using it correctly.

My best guess is that what he meant to tell you was to run```
sudo fdisk -l /dev/sda
```

---

### Post by rafaelous on 2009-10-07
Hmm, that makes it even stranger from my point of view because I did like you said and got:
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21621   173670651    7  HPFS/NTFS
/dev/sda3           21622       30342    70051205+   7  HPFS/NTFS
/dev/sda4           34017       60788   215040000    7  HPFS/NTFS
```and then when I open up GParted this is what I'm seeing
[IMG]http://i34.tinypic.com/2lt0z2b.png[/IMG]
which is the complete opposite.

---

### Post by mechro on 2009-10-07
I'm not sure but the HPFS/NTFS file system could be the clue. Is it a manufacturers set up to include a recovery partition?

If it was me I would back up Windows, wipe the drive and start again... **BUT THAT IS PROBABLY GOING OVER THE TOP** so best to wait for more advice and do some more research.

---

### Post by rafaelous on 2009-10-07
Funny you say that actually

It was that way, but I have reformatted the HDD since I got it, so there isn't one anymore on it. When I tried to install Ubuntu first time round about 6 months ago I reformatted the HDD and installed linux, but then when i tried to install windows (if i remember correctly) windows said the HDD was unallocated space.

I may as well reformat the entire thing sometime anyway when I make the switch from Vista, but I'd want to be sure that I could get everything working in a day, because I'm not the only one who uses the PC.

---

### Post by alphaniner on 2009-10-07
More strange than you probably realize, I wager.  Notice the second line of the **fdisk** output reads '30394 cylinders'.  The 'Start' and 'End' fields of your partitions are in units of cylinders.  However, sda4 apparently starts beyond the cylinder boundary:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21621   173670651    7  HPFS/NTFS
/dev/sda3           21622       30342    70051205+   7  HPFS/NTFS
/dev/sda4           **34017       60788**   215040000    7  HPFS/NTFS
```

What is the output of **sudo fdisk -l /dev/sdb**?  And what does GParted show when you select /dev/sdb?  Any chance for a screeny from Windows Disk Management?  You don't have any kind of RAID setup do you?

---

### Post by mechro on 2009-10-07
It was the "HPFS" that got me. Perhaps fdisk reports standard NTFS as HPFS/NTFS... I don't have an NTFS partition to check.

It's unusual for GParted to do this with a standard installation so perhaps you have a faulty drive or an error crept in during your last format.

---

### Post by alphaniner on 2009-10-07
Nah, HPFS/NTFS is the normal designation for NTFS partitions.  If you're curious, you can open a disk with cfdisk and select Type to see all the possible partition types.

---

### Post by mechro on 2009-10-07
> **alphaniner said:**
> Nah, HPFS/NTFS is the normal designation for NTFS partitions.  If you're curious, you can open a disk with cfdisk and select Type to see all the possible partition types.

Thanks.

Ahh... Yes... **07 HPFS/NTFS**... No NTFS on its own.

:)

---

### Post by rafaelous on 2009-10-07
> **alphaniner said:**
> What is the output of **sudo fdisk -l /dev/sdb**?  And what does GParted show when you select /dev/sdb?  Any chance for a screeny from Windows Disk Management?  You don't have any kind of RAID setup do you?

Hmm, yea that is rather strange.
So I've tried for the output of , and I'm getting:
```
Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01000100

Disk /dev/sdb doesn't contain a valid partition table

```
In GParted I'm getting, exactly the same for /dev/sdb as /dev/sda that's why i didn't bother taking a screenie and all that. 

[s]I'll boot up into Windows and get a screenie of that and edit then edit this post.[/s]Screenie added in.
[IMG]http://i33.tinypic.com/zwhml4.png[/IMG]

---

### Post by alphaniner on 2009-10-07
Yeah, you've got a RAID 0 or something similar.  I didn't think the partition table would be legible on a RAID 0, but I could be wrong.  Notice that Disk Management shows one drive of 465.66 GB, whereas GParted shows two drives of 232.83 GB.  And 232.83 * 2 = 465.66.  As to what is controlling it, I dunno.  I would say it's software controlled, but I didn't think such a thing was bootable.

---

### Post by rafaelous on 2009-10-07
> **alphaniner said:**
> Yeah, you've got a RAID 0 or something similar.  Notice that Disk Management shows one drive of 465.66 GB, whereas GParted shows two drives of 232.83 GB.  And 232.83 * 2 = 465.66.  As to what is controlling it, I dunno.  I would say it's software controlled, but I didn't think such a thing was bootable.

So what would be the best option now? Restore with GParted and leave as 2 seperate disks? Isn't it anyway a better idea to put an OS on each disk rather than all one virtual disk and different partitions. Also, is it worth or should i be checking in the BIOS menu whether there actually are 2 HDD's because I'm pretty sure that last time I opened it up there was only 1.

---

### Post by alphaniner on 2009-10-07
I'd trust your eyes over my divinations, but if there really is only one HDD then I don't know what to tell you.  That said, I think it's worth a look in the BIOS at least.  If you find there are two and they are SATA, what mode is the SATA controller in?  Don't change anything though because it would probably bork your Windows.

You could also look in installed programs and in Device Manager.

If there's only one drive, then you should figure out why all the Linux tools are seeing two drives before you install Ubuntu.  If there are two drives you should figure out why/how Windows is seeing them as one drive if you intend to dual boot with Ubuntu.

I'm going to lunch soon, but I'll be back in 1hr.

---

### Post by rafaelous on 2009-10-07
OK, the BIOS seems to agree with you that there are 2x250gb HDD's.

I'm gonna start trawling through google for why that is. I'll post back here any progress I make.

---

### Post by alphaniner on 2009-10-07
What is the make/model of your mobo?  I'm willing to bet that there is a setting in your BIOS which will determine how your drives are accessed (again, if they are SATA).  For example, on a newer ASUS mobo, I have two settings for SATA: 'SATA Configuration' which can be Disabled/Compatible/Enhanced and 'Configure SATA as' which can be IDE/RAID/AHCI.  I have them configured as Enhanced:IDE.  But it can vary widely from manufacturer to manufacturer.  If you know what mobo you have maybe I can dl the manual and tell you what to look for.

---

### Post by mechro on 2009-10-07
*Off-topic*

Hmmm, this offering help and advice malarkey is harder than I thought.

Dual-booting RAID is unknown territory for me. If I can't jump into the comfy GUI of Gparted then I'm kinda lost.

Apologies to rafaelous for being of little help.

Apologies to alphaniner for coming across as an ignorant jerk.

:)

---

### Post by alphaniner on 2009-10-07
Ignorant jerk?  Hogwash and poppycock.

Honestly, I'm just keeping this thread alive until someone who *really* knows what they're talking about swoops in and solves it in one sentence. :)

---

### Post by rafaelous on 2009-10-07
@mechro no worries, i can't help much either with this :P

Back on topic again, I popped onto some random IRC channel and found out pretty much everything. Basically it was using RAID 0 and I've found how to get rid of that and I'm gonna do that tomorow once I've backed up everything I want to keep. Of course I'll let you guys know how it goes :)
If you want here's a pastie of my IRC conversation about it. [http://pastie.org/645776](http://pastie.org/645776)

Going off topic again, I actually really like it here, people seem nice and all that, I'll probably be here to help and stay once I know a bit more about this subject.

---

### Post by alphaniner on 2009-10-07
I'm glad you were able to figure it out.  I read your IRC chat and I had a <doh!> moment... I should have mentioned the RAID setup during POST.  However, I still recommend you go into the BIOS and see if you can change the SATA mode to something other than RAID.  It just seems a sensible thing to do if you aren't going to be using the functionality.  RAID is great if you use a dedicated controller, but I stay away from mobo onboard RAID regardless of the OS.  Good luck.

Also be sure to mark the thread as Solved using the 'Thread Tools' near the top.

---

### Post by rafaelous on 2009-10-07
Yupp, thanks for that. I'll have a look into that, just trying to get hold of an HDD for a day to backup all the stuff i want to keep whilst i restore.

---

### Post by Divinjohn on 2009-11-11
I have the same problem.
> 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90272f20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15735636    7  HPFS/NTFS
/dev/sda2            1960       24321   179622765    f  W95 Ext'd (LBA)
/dev/sda5            1960       21710   158649876    7  HPFS/NTFS
/dev/sda6           21711       24207    20057121   83  Linux
/dev/sda7           24208       24321      915673+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aecee65

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2611    20972826    f  W95 Ext'd (LBA)
/dev/sdb2   ?        2612       38913   291595783+   7  HPFS/NTFS 

In Gparted my sdb comes as totally unallocated.! I have no clue. I have 2 Hard drives. I am on Intel DG35EC board .!

---

