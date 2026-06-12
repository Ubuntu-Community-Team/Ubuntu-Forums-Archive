---
title: "Gparted won't format harddrive"
date: 2010-03-17
forum: General Help
---

### Post by Weidbrewer on 2010-03-17
I tossed a 500GB hard drive into my machine (Ubuntu 64 8.10) so that I could back some files up.  This drive when last used was part of a software RAID (no longer in use.)  I deleted the partition that was on it, and tried to reformat using Gparted to ext3...but it won't work.

The only error message I get is that it failed.  Details do not provide any additional information.

I went to the command line and attempted to mount it just to see what would happen, and I got this:

```
~$ sudo mount /dev/sde1 /media/backup1
mount: unknown filesystem type 'linux_raid_member'

```

Apparently, it still thinks it's part of the RAID.  What can I do to erase and reformat this drive?

---

### Post by audiomick on 2010-03-17
yes, gparted can have problems with drives that were in raid arrays. I haven't encountered it, only read about it, and I can't remember what the solution was off hand. Try searching the forum for "gparted raid" or similar. Something should turn up, I think.

---

### Post by prodigy_ on 2010-03-17
Type ```
sudo parted /dev/sde
``` in terminal. In [parted] prompt type ```
print
``` to see the numbers of all existing partitions on /dev/sde. Then type ```
rm <number>
``` for the partition you want deleted.

**As always, be VERY careful with partitioning. If you're unsure, better post the output of "print" command here.**

---

### Post by Weidbrewer on 2010-03-17
> **audiomick said:**
> yes, gparted can have problems with drives that were in raid arrays. I haven't encountered it, only read about it, and I can't remember what the solution was off hand. Try searching the forum for "gparted raid" or similar. Something should turn up, I think.


Hmmm...yeah, I Googled before I came here, and most responses are "sorry, Gparted doesn't support RAID."  Unable to find any way around it.  I checked, and removing the partition seems to have removed the RAID flag as well.  Drat.


> **prodigy_ said:**
> Then type ```
rm <number>
``` for the partition you want deleted.


I can remove the partition without issue (Through Gparted, and then with your instructions just to be sure.)  The problem is that I can't format the disk.  I don't feel like opening a Windows box and slapping it in there, but I guess that might be the only recourse.

---

### Post by prodigy_ on 2010-03-17
Ok. :-) Then have you tried CLI parted "mkfs" command to format the partition? Maybe this will at least give you a more specific error message.

---

### Post by Weidbrewer on 2010-03-17
> **prodigy_ said:**
> Ok. :-) Then have you tried CLI parted "mkfs" command to format the partition? Maybe this will at least give you a more specific error message.

Not very familiar with that command.  If it helps, the output in Gparted reads:

```
mkfs.ext3 -L "" /dev/sde1
```

Is that the same command I should try running?

---

### Post by srs5694 on 2010-03-17
You could also try this:

```

sudo dd if=/dev/zero of=/dev/sde bs=1024 count=10240

```

This copies 10MB of 0 values to the hard disk. It should wipe out the partition table (you'll need to create a new one) and a big chunk of the first partition. If this doesn't work, try increasing the count value. If necessary, omit the count parameter altogether and this will wipe out the entire hard disk -- but that could take hours.

There's nothing magical about RAID. It's all just 1s and 0s, so blanking it out should do the trick.

---

### Post by Weidbrewer on 2010-03-17
> **srs5694 said:**
> You could also try this:

```

sudo dd if=/dev/zero of=/dev/sde bs=1024 count=10240

```

This copies 10MB of 0 values to the hard disk. It should wipe out the partition table (you'll need to create a new one) and a big chunk of the first partition. If this doesn't work, try increasing the count value. If necessary, omit the count parameter altogether and this will wipe out the entire hard disk -- but that could take hours.

There's nothing magical about RAID. It's all just 1s and 0s, so blanking it out should do the trick.

No luck.  The command seems to run, but then gparted still doesn't work.

I ran:

```
sudo mke2fs -j /dev/md0
```

I got a message that "/dev/sde is apparently in use by the system; will not make filesystem here."

---

### Post by srs5694 on 2010-03-18
re: Using dd...

> **Weidbrewer said:**
> No luck.  The command seems to run, but then gparted still doesn't work.

Did you try increasing the count value? I don't happen to know offhand where RAID information is stored, so I just picked a nice big round number. Maybe you need a bigger value. Letting it run on the whole drive (omitting count and its value entirely) will definitely zero out the drive, leaving no trace of any previous use on it. OTOH, if the RAID setup is active when you do this, the RAID subsystem might try writing enough RAID data when you shut down to cause grief later....

Check to see if there's a /dev/md0 device file. If there is, try to deactivate it before doing anything else. It's been a while since I used RAID, but I believe that "mdadm -S /dev/sde1" (changing /dev/sde1 to whatever partition on /dev/sde is the RAID partition) should do the job.

> I ran:

```
sudo mke2fs -j /dev/md0
```I got a message that "/dev/sde is apparently in use by the system; will not make filesystem here."

You definitely don't want to be doing anything with /dev/md0; that's the way to address the RAID device as Linux sees it, not the underlying physical device. Any operations, aside from anything required to shut down the RAID array, should be done on /dev/sde or its partitions, not /dev/md0.

Here's another idea: Grab a [FreeBSD](http://www.freebsd.org) install disc and use it to wipe the drive. Since FreeBSD does not (AFAIK) understand Linux RAID setups, you shouldn't have problems with it activating the RAID device. FreeBSD is pretty similar to Linux in many respects; you can use dd, for instance, to write zero values to the drive. You'll need to use a different device identifier, though (/dev/ad0 and up or /dev/da0 and up, depending on drive type). FreeBSD's text-mode disk partitioning tools are different, too; I believe they use one called fdisk, but it works very differently from Linux's fdisk. In principle, you could do something similar with [FreeDOS,](http://www.freedos.org) but I don't know if it comes with a dd equivalent, and I don't know how its FDISK tool would treat Linux partitions.

---

### Post by srs5694 on 2010-03-18
Further to my last suggestion: There's a downloadable disc image called [Ultimate Boot CD](http://www.ultimatebootcd.com/) that contains a lot of free (mostly DOS-based) disk and system diagnostic and recovery tools. These include disk utilities that can completely blank a hard disk. If one of those doesn't work, then there's something very weird indeed going on.

---

### Post by Weidbrewer on 2010-03-18
> **srs5694 said:**
> re: Using dd...



Did you try increasing the count value? 

Yes, I wrote 512MB to the disk with the same logic you had - still no dice.

> Check to see if there's a /dev/md0 device file. If there is, try to deactivate it before doing anything else. It's been a while since I used RAID, but I believe that "mdadm -S /dev/sde1" (changing /dev/sde1 to whatever partition on /dev/sde is the RAID partition) should do the job.  

I had tried that as well, and I don't remember the error I got, but it was something to the effect that mdadm didn't apply to it.



> You definitely don't want to be doing anything with /dev/md0

Wow...I have no idea why I wrote that.  I ran that command on /dev/sde.  I think it was because I was also looking at something on my screen that had to do with a RAID that I *do* have running on that machine.  Sorry for the confusion.

> Here's another idea: Grab a [FreeBSD](http://www.freebsd.org) install disc and use it to wipe the drive. 

I'll think about it with that and the UBC.  With the later, I needed it for something else not long ago, and I didn't have much luck finding it.  Most of the sites I googled when to dead links and broken mirrors.  Didn't seem like anyone was maintaining it any more.  Thanks for the help.

---

### Post by srs5694 on 2010-03-18
As a test, I just downloaded Ultimate Boot CD via BitTorrent from the link on the page I referenced earlier. There were 25 peers and it downloaded in about a minute.

---

### Post by Weidbrewer on 2010-03-19
Okay, good news: I have the disk and have begun the wipe process.

Bad news: I just used the first one on the list (boot and nuke) and started it before I went to bed.  It's been running 11 hours now and is only 1.39% done.  Looks like I set it to three-pass, which with two 500GB drives will take forever and a day.

Is there any way to safely quit this (without damaging hardware) so that I can run a different one?  Basically, is there a quit command (like ctrl+c) or will I have to do a hard reboot?

---

### Post by srs5694 on 2010-03-19
Just do a hard reboot; it shouldn't damage the hardware. I might try it in Linux at this point; it's conceivable (perhaps even likely) that the utility has wiped enough of the hard disk to overcome the problem already.

---

### Post by Weidbrewer on 2010-03-19
Great - your response came just in time for me to get home from work and back up the conclusions I came to today (both on the boot and the important sectors being blanked.)  I'll go give it a try.

---

### Post by Weidbrewer on 2010-03-19
And the answer is...no, it did erase it enough.  Doing a quick pass now.

---

### Post by Weidbrewer on 2010-03-20
Good to go.  Thanks for all the help.

---

