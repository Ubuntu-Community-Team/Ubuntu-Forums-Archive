---
title: "New to Ubuntu install"
date: 2011-01-06
forum: General Help
---

### Post by Redding on 2011-01-06
Okay...it started with rooting my Motorola Droid. I got quite interested in the whole rooting/linux "world". The only problem is, my hands move A LOT faster than my brain does. I'm an "educated novice" at best when it comes to all of this and still learning slowly, but surely. 

I followed an online tutorial and before I realized quite what i'd done, I had dual installed Ubuntu linux 10.10 on my laptop. ISO'd this, partitioned that and realized....i'm in way over my head. Then I started researching how to just go back in time and get my "safe" windows vista back until I'm ready to make the switch to linux and just ended up getting more confused. 

 I just need all kinds of help. How do I actually BOOT into Windows on a dual boot computer that I apparently just created? 
How, if need be, do I undo everything I just did in the past few hours and careless tinkering?
If I decide to stay with Linux, how do I get my damn wireless router to recognize?

I'm just lost and overwhelmed.....HELP!!!

---

### Post by Pollox on 2011-01-06
Okay, there's a lot of questions there. Let's tackle some.

First, backup your data. Before doing any further tinkering, make sure you backed up anything you don't want to lose, if you haven't done so already.

Assuming you actually set up a dual boot properly (the installer should have walked you through that), and didn't just wipe out Windows entirely, you should be greeted with a menu at boot up time asking you to pick an OS. Do you see such a menu? Is Windows in that list?

See this article [https://help.ubuntu.com/community/RecoveringWindows#Reinstating](https://help.ubuntu.com/community/RecoveringWindows#Reinstating) Windows about restoring your Windows install to use the full disc (assuming it still exists).

Make a separate post about your wireless router and describe your problem in detail.

---

### Post by Redding on 2011-01-07
Alright.....first of all, thanks for the reply. 
Let's start from the beginning. At this point I'm not even sure how to get back into Windows. To answer your question, I installed a dual boot just as the installer instructed. When given the option to allocate space for the linux hard drive, I dragged the partition bar over to give linux right at 20GB on the hard drive. The remaining 60Gb said Windows Vista inside of it. The process then proceeded as normal and.....BOOM, i've got linux. I guess i'm just a little overwhelmed because linux booted up perfect, but was SO INCREDIBLY different....not bad, just different.....I panicked and tried desperately to just make it all go away. I'm better this morning....now more just curious as to my next move. Thanks again for the reply. Look forward to more advice.

---

### Post by cmoraes on 2011-01-07
Hi Redding,

In order to get back into Windows - 
- restart your computer
- after the BIOS info, you should see a screen which lists a few options of Ubuntu and your Windows OS (probably at the bottom)
- you can use your arrow keys to navigate and select your windows OS. Press Enter.
- your Windows OS should now boot normally.

Note: the screen you see with the options of the OS is called the 'grub' screen.

HTH.

---

### Post by mikewhatever on 2011-01-07
> **Redding said:**
> Alright.....first of all, thanks for the reply. 
Let's start from the beginning. At this point I'm not even sure how to get back into Windows. To answer your question, I installed a dual boot just as the installer instructed. When given the option to allocate space for the linux hard drive, I dragged the partition bar over to give linux right at 20GB on the hard drive. The remaining 60Gb said Windows Vista inside of it. The process then proceeded as normal and.....BOOM, i've got linux. I guess i'm just a little overwhelmed because linux booted up perfect, but was SO INCREDIBLY different....not bad, just different.....I panicked and tried desperately to just make it all go away. I'm better this morning....now more just curious as to my next move. Thanks again for the reply. Look forward to more advice.

Let's see what partitions are there on the hdd. From Ubuntu, open Applications->Accessories->Terminal, and post the output of the following command:

```
sudo fdisk -l #<-that is an L, not a one
```

---

### Post by Redding on 2011-01-07
> **mikewhatever said:**
> Let's see what partitions are there on the hdd. From Ubuntu, open Applications->Accessories->Terminal, and post the output of the following command:

```
sudo fdisk -l #<-that is an L, not a one
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x98b04802

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4750    38146230    7  HPFS/NTFS
/dev/sda2            4750        9730    40002561    5  Extended
/dev/sda5            4750        9520    38316032   83  Linux
/dev/sda6            9520        9730     1685504   82  Linux swap / Solaris


I finally figured out how to boot back into Windows and it worked fine. Above is the information asked for. I got to looking around as far as partitions and hard drives and whatnot.....the thing that confuses me is this...I remember specifically allocating 20gB of my hard drive for Linux. When I check the partitions, i'm showing a section of hard drive that reads "linux" and it is almost 40gB.......ummmmm.......WHY? 
Thanks for all of the help so far guys.

---

### Post by Redding on 2011-01-08
Anyone have any ideas on my hard drive issue? I wasn't planning on allocating THAT much hard drive space to linux. Kind of has me nervous.

---

### Post by Redding on 2011-01-09
Anyone? Anyone? Bueller?

---

### Post by Pollox on 2011-01-09
So the only thing left is that you allocated more to linux than you intended, and you want to shrink that space?
Options you have:
1) leave it as it is, unless you're short on space in Windows
2) Boot into Windows and use its partitioner to delete the linux partitions and expand your Windows partition to the size you want. Then reinstall Ubuntu using the free space you left.
3) Boot from a live cd, and use gparted to shrink the Ubuntu partition and expand the Windows partition.

I recommend (2), because (3) is slow, and assuming you haven't done much with Ubuntu yet it shouldn't be much trouble to reinstall. Please back up your data before doing any partitioning, as there's always the potential for data loss (either through software or accidentally deleting the wrong partition).

---

### Post by Redding on 2011-01-09
Okay....Pollox...thanks so far. Option #2 sounds like all that I need to do. I went into my partitioner and saw the following:

- C: 36.38GB NTFS, Healthy, (System, Boot, Page File, Active, Crash Dump, Primary Partition)

- 36.54GB Healthy, (Primary Partition)

-1.61GB Healthy (Primary Partition)

So....it does seem like the partition I created for Linux has doubled for some reason. I am assuming that the first partition listed under C: drive is my windows partition. What would be my next step from here. Like I said, I know just enough about this stuff to get myself into trouble. Thanks so far for your help.

---

### Post by Pollox on 2011-01-09
The next step would be to burn a live cd if you don't have one already. Select the "try Ubuntu without installing" option. Then go to System > Administration > Gparted partition editor. We'll use that for repartitioning. (I mentioned something about using the Windows partition editor, but you can't resize the Windows partition while you're using it, so ignore that.)

That NTFS partition is the Windows one. So, you'll want to delete the other two, and resize the Windows partition to whatever size you wanted it. See this documentation: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) and let us know if you get stuck.

Once that's done, reinstall Ubuntu. There should be an option to just use the free space you left.

---

