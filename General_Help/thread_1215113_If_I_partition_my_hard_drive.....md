---
title: "If I partition my hard drive...."
date: 2009-07-16
forum: General Help
---

### Post by TF2-Engi on 2009-07-16
Will I lose all my data from XP?  I don't have a portable hard drive so I can't back everything up and I think I read it erases your hard drive if you choose to partition it.  I have 250 gigs that I can't really afford to lose...

Thank you!

---

### Post by perrti-y02 on 2009-07-16
It depends how you do it. If you have no way of backing up data then it probably isn't a great idea but is doable if you know what you are doing. Do you have a spare hard drive that you could experiment with?

---

### Post by merlinus on 2009-07-16
You can select side-by-side from the partitioning menu, and use the sliders to determine the space for each.  Be sure to delete temp and other unneeded files and defrag windows several times first.

---

### Post by TF2-Engi on 2009-07-16
> **perrti-y02 said:**
> It depends how you do it. If you have no way of backing up data then it probably isn't a great idea but is doable if you know what you are doing. Do you have a spare hard drive that you could experiment with?

No, at the moment I don't.  I am using the partitioner that ubuntu has in the process of installing it.  I don't know how reliable it is to keeping your data.  Thank you.

---

### Post by perrti-y02 on 2009-07-16
I have never had a problem and I have done many resizes and suchlike. There is no guarantee that it won't eat everything but I think it is unlikely.

---

### Post by Monotoko on 2009-07-16
It is very unlikley that it will eat your data, but not impossible. You must be prepared for the tiny chance you may lose everything when dealing with partitions.

I once had a problem when the power decided to cut while i was partitioning, i lost everything.

---

### Post by nerdzero on 2009-07-16
I always did backups before resizing my partitions and never had a problem.  Then one time I did not do a backup because I had never had any problems before...long story short, I lost two partitions and had to spend a few hours restoring from old backups.

Always backup your important data!

---

### Post by TF2-Engi on 2009-07-16
> **Monotoko said:**
> It is very unlikley that it will eat your data, but not impossible. You must be prepared for the tiny chance you may lose everything when dealing with partitions.

I once had a problem when the power decided to cut while i was partitioning, i lost everything.


Yeah, I know there's that fraction of a chance that it might delete everything that's what I am scared of.  I am using the installer in Ubuntu, partitioning it using the slider thing they have provided.  I am using 9.04 by the way.  Thank you all!

---

### Post by itsjareds on 2009-07-16
Partitioning is generally safe if you use the safest methods. Here's a step-by-step walk through:

1. Disable your paging file on Windows. This file is stored at the end of your hard disk, which makes partitioners throw errors about files being at the end.

2. Download and install [PerfectDisk]("http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/free-trial") (free trial). This is a defragmenter for Windows that can consolidate your free space, which means that it moves all of your files to the front of the drive. This lets you shrink the partition to create another.

3. Run PerfectDisk and start the defragment on your Windows partition. Make sure you select the setting to Consolidate Free Space. This may take a while, so be patient.

4. The next step is to defragment your system files. This has to be done after a reboot, and PerfectDisk will run in a command prompt-style similar to Microsoft's chkdsk. To defragment your system files, click the button at the top labeled System Files. You'll get a popup asking to schedule the defragment for the next reboot, click Yes.

5. Reboot your computer. The PerfectDisk defragmenter will run.

6. Once you're back in Windows, open PerfectDisk again and analyze your drive. All of the blocks should be towards the top. If there are any files at the bottom, you'll only be able to resize up to that point on the drive.

7. If you still see some blocks at the bottom, post back here. If everything looks good, you can go back to your Ubuntu installer and run their partition tool. Resize your Windows partition to give yourself a little wiggle room for Windows, then you'll be left with a bunch of "Unallocated space". Create a partition here of type ext3.

8. Select that ext3 partition for installation, and you should be good to go. The rest of the installer is relatively trivial. Post back if you run into any problems.

---

**Just be careful: DO NOT move your Windows partition, only resize it. Moving a partition can cause file corruption. Also, make sure that you NEVER try to format your Windows partition. This'll clear all of your data.**

---

### Post by TF2-Engi on 2009-07-16
> **itsjareds said:**
> Partitioning is generally safe if you use the safest methods. Here's a step-by-step walk through:

1. Disable your paging file on Windows. This file is stored at the end of your hard disk, which makes partitioners throw errors about files being at the end.

2. Download and install [PerfectDisk]("http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/free-trial") (free trial). This is a defragmenter for Windows that can consolidate your free space, which means that it moves all of your files to the front of the drive. This lets you shrink the partition to create another.

3. Run PerfectDisk and start the defragment on your Windows partition. Make sure you select the setting to Consolidate Free Space. This may take a while, so be patient.

4. The next step is to defragment your system files. This has to be done after a reboot, and PerfectDisk will run in a command prompt-style similar to Microsoft's chkdsk. To defragment your system files, click the button at the top labeled System Files. You'll get a popup asking to schedule the defragment for the next reboot, click Yes.

5. Reboot your computer. The PerfectDisk defragmenter will run.

6. Once you're back in Windows, open PerfectDisk again and analyze your drive. All of the blocks should be towards the top. If there are any files at the bottom, you'll only be able to resize up to that point on the drive.

7. If you still see some blocks at the bottom, post back here. If everything looks good, you can go back to your Ubuntu installer and run their partition tool. Resize your Windows partition to give yourself a little wiggle room for Windows, then you'll be left with a bunch of "Unallocated space". Create a partition here of type ext3.

8. Select that ext3 partition for installation, and you should be good to go. The rest of the installer is relatively trivial. Post back if you run into any problems.

---

**Just be careful: DO NOT move your Windows partition, only resize it. Moving a partition can cause file corruption. Also, make sure that you NEVER try to format your Windows partition. This'll clear all of your data.**

I already defragged when I was in windows, I just used the windows one, but now I am in Ubuntu typing to you guys with the 4th step "Prepare disk space" page running.  That's where I am stuck...I don't want to lose any data but I don't own a portable hard drive.

---

### Post by TF2-Engi on 2009-07-16
[http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

This guide says in red that all data will be erased from the hard drive, is it saying that if you format it to delete windows or if you use both os's?

---

### Post by itsjareds on 2009-07-16
Ok. I didn't backup my files either when I installed Ubuntu in a third partition. I had two other Windows partitions (XP and 7). I just resized both of my other partitions and I was able to create a third ext3 partition with the free space.

Just make sure you resize your Window's partition and don't do anything else to it. Moving the partition is really error prone (It corrupted my Windows 7 partition). Resizing a partition should be safe enough.. just be sure that you don't have any files at the end of your partition (the partitioner will stop and won't overwrite if you do).

---

### Post by itsjareds on 2009-07-16
> **TF2-Engi said:**
> [http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

This guide says in red that all data will be erased from the hard drive, is it saying that if you format it to delete windows or if you use both os's?

The author meant that once you've created another partition, you'll have two. Make sure that you don't select to install into your Windows partition. Install into the empty partition. It'll format that partition (clear all contents) and begin installing Ubuntu.

---

### Post by TF2-Engi on 2009-07-16
> **itsjareds said:**
> Ok. I didn't backup my files either when I installed Ubuntu in a third partition. I had two other Windows partitions (XP and 7). I just resized both of my other partitions and I was able to create a third ext3 partition with the free space.

Just make sure you resize your Window's partition and don't do anything else to it. Moving the partition is really error prone (It corrupted my Windows 7 partition). Resizing a partition should be safe enough.. just be sure that you don't have any files at the end of your partition (the partitioner will stop and won't overwrite if you do).

By resizing you guys are saying that in the installation setup you pick the "Install them side by side, choosing between them each startup" option?  Then you take the slider and choose how many gigs for XP/Vista/7 etc and how many for Ubuntu?  Thank you!

---

### Post by nerdzero on 2009-07-16
Yes, that is the option you want in this case.  If you follow itjareds suggestions you will most likely be okay.  However, I personally don't recommend to anyone not to do backups.  Is compressing your data and burning it to DVDs an option?

---

### Post by TF2-Engi on 2009-07-16
> **nerdzero said:**
> Yes, that is the option you want in this case.  If you follow itjareds suggestions you will most likely be okay.  However, I personally don't recommend to anyone not to do backups.  Is compressing your data and burning it to DVDs an option?

We have 700 mb cd's in my house somewhere, if I can compress 250 gbs on it by all means I will...lol.  I don't think it will work for me though.  I am trying to follow itjareds suggestions but I am getting confused, but it certainly isn't his fault.  Right now I am on the step I stated, I moved the slider at the bottom to 335.0 Gb XP Professional, 130.8 Gb Ubuntu 9.04, and it has 7.4 mb of free space???...I have a 500 gb hard drive with 47 percent free but it actually on has 465 gigs so if you multiply them together I have 218.55 gigs left so if I am doing it right I should be ok.  Thanks!

---

### Post by TF2-Engi on 2009-07-16
Guys should I continue from Step 4 "Install them side by side, choosing between them at startup"?  Then I put the slider at 335.0 GB XP, 130.8 GB Ubuntu 9.04, and it has 7.8 mb free space?

---

### Post by TF2-Engi on 2009-07-16
Please guys I need to know if I can continue on the step I stated or if I should just restart my computer.  Thank you, sorry if I sound rude I don't know how long the installer can sit though....

---

### Post by TF2-Engi on 2009-07-16
Bump

---

### Post by TF2-Engi on 2009-07-16
Should I use Wubi in windows or should I continue at the step I am at?

---

### Post by merlinus on 2009-07-16
Continue.  Be bold...

---

### Post by TF2-Engi on 2009-07-16
> **merlinus said:**
> Continue.  Be bold...

I want to but you think it is mildly safe to continue?  Thanks!

---

### Post by CatKiller on 2009-07-16
> **TF2-Engi said:**
> Guys should I continue from Step 4 "Install them side by side, choosing between them at startup"?  Then I put the slider at 335.0 GB XP, 130.8 GB Ubuntu 9.04, and it has 7.8 mb free space?

That sounds about right. You don't necessarily need that much for Ubuntu. Anything over about 40 GiBs should be sufficient for a dual-boot, but if you've got the free space then go for it.

EDIT: The free space is because partitions have to start and end on particular boundaries. Sometimes the size of the partitions that you choose mean that that doesn't quite work out, and so the partitions are made a fraction smaller and you get a tiny sliver that you can't allocate to the partitions either side. Don't worry about it.

---

### Post by merlinus on 2009-07-16
Decide what is the worst thing that can happen, and if it is worth the risk.  You won't die, in any event.

OTOH, you may be thrilled to death with the outcome!

---

### Post by TF2-Engi on 2009-07-16
OK I am going for it....hopefully it works thanks!

---

### Post by TF2-Engi on 2009-07-16
"Before you can select a new partition size, any previous changes have to be written to disk.

You cannot undo this operation.

Please note that the resize operation may take a long time"

Continue????

---

### Post by TF2-Engi on 2009-07-16
If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #6 of SCSI1 (0,0,0) (sda) as swap




CONTINUE???? This is the final step...

---

### Post by merlinus on 2009-07-16
Looks great to me!  Notice that it is NOT going to format windows.

---

### Post by TF2-Engi on 2009-07-16
> **merlinus said:**
> Looks great to me!  Notice that it is NOT going to format windows.

OK that's good, I am just a nervous wreck because I lost everything once because a friend gave me a LEGAL copy of Vista but it was out of uses so I lost hours of gameplay in a number of games.  Thank you.  I will install it and see my results.

---

### Post by itsjareds on 2009-07-16
If you have some really important data you want to keep, why not make backups of a very select few files? I'm sure if you saved those few files it would be worth something if your hard drive got reformatted.

---

### Post by TF2-Engi on 2009-07-16
> **itsjareds said:**
> If you have some really important data you want to keep, why not make backups of a very select few files? I'm sure if you saved those few files it would be worth something if your hard drive got reformatted.

It installed fine, so far so good, xp still seems to be working good to, thank you everyone!!!!!

The best program to get steam running is WINE right?

---

### Post by CatKiller on 2009-07-17
> **TF2-Engi said:**
> It installed fine, so far so good, xp still seems to be working good to, thank you everyone!!!!!

Glad to hear it.

> The best program to get steam running is WINE right?

Wine (or one of its variants, like Crossover) is the only way to make Windows executables work on Ubuntu. If you run into any trouble with Wine it's best to start a new thread.

---

### Post by itsjareds on 2009-07-17
Or if you have plenty of RAM (and CPU power) you can install the Windows 7 RC inside Virtualbox, then run whatever Windows programs you want.

---

### Post by TF2-Engi on 2009-07-17
> **itsjareds said:**
> Or if you have plenty of RAM (and CPU power) you can install the Windows 7 RC inside Virtualbox, then run whatever Windows programs you want.

I have a Core 2 Quad and 4 gbs of ram but I lost my Windows 7 beta disk....but I did preorder windows 7.

---

### Post by itsjareds on 2009-07-17
Microsoft still lets you download Windows 7 RC for free.

[URL="http://www.microsoft.com/windows/windows-7/download.aspx"]
Download Windows 7 (scroll down the page a bit)[/URL]

The offer's still available until August 20, and I'm sure that people will still be distributing it through torrents. I saved 30 product keys to give to people if they need to activate it after August 20.

---

