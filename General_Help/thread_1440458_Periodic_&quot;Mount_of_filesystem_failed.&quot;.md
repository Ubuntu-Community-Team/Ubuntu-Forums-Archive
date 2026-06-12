---
title: "Periodic &quot;Mount of filesystem failed.&quot;"
date: 2010-03-27
forum: General Help
---

### Post by jason102 on 2010-03-27
Hi guys, 

I've been having this one annoying problem that's been plaguing me ever since I installed 9.10 - every now and then Ubuntu will fail to boot or load and throw at me this fantastic message:
> Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
 * Starting init crypto disks... [ OK ]
root@jason-desktop:~#

A couple months ago when this first occurred I researched the issue and discovered that by booting into the live cd and using the following fsck command I could temporarily correct the problem and be able to boot into Ubuntu fine for some time:
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Superblock last mount time (Tue Mar 23 15:09:05 2010,
	now = Mon Mar  3 03:16:44 2003) is in the future.
Fix<y>? yes

/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 231123/30146560 files (0.2% non-contiguous), 4306006/120585890 blocks
ubuntu@ubuntu:~$
```

With this done, I would be able to load and login to my session as if nothing was wrong. Unfortunately, after a seemingly random/spontaneous number of logins/boots later, I'd get the same mount of filesystem failed error once again and would be forced to used the live cd and the fsck command, again. By the way, is that statement about the "superblock mount time is in the future" telling me what my overall issue is that must be fixed?

I'm now tired of this silly routine and would like to figure out what's wrong and put an end to it once and for all. A week ago I reinstalled my system with the latest stable version of Ubuntu 9.10 thinking this would fix the issue, but it didn't - I've had to use fsck from the live cd now 2 times since then in order to access my data and boot correctly. When I reinstalled Ubuntu I told the live cd installer to completely format and use my entire disk for the new OS, but even wiping the thing clean and installing from scratch didn't seem to solve my problem. 

There are 2 things that I think may be connected to this issue:
1) For some reason when I boot and login gnome-panel will fail to load correctly and be frozen until I use the following to reset the thing:
```
killall gnome-panel
```

This as well happens randomly it seems and occurs irregularly. It's just that I think whatever data is corrupted or whatever might be connected to these improper loads of gnome-panel.

2) Could the fact that I started using the new feature 9.10 offers, the one that allows you to encrypt your home folder, be an issue? I haven't tried reinstalling the system without choosing that option, but could this be a source of my problems?

So, what advice might you guys have for me? Thanks so much,
jason102

---

### Post by RedRat on 2010-03-27
Based on this info, it sounds suspiciously like an impending hard drive failure. Sounds as if files are not being written to completion or errors on the disk. To be safe and prudent, you might want to back up any data files, just in case. 

Hard drives do fail, even new ones.

---

### Post by jason102 on 2010-03-27
Huh, ok well thanks for letting me know. Fortunately I had to back everything up for that recent reinstall a week ago and haven't done much with this system since. This drive is now about 1 and a half years old, a 500GB Seagate 7200 rpm drive. I only have the one hard drive for this computer. 

Would there be a way for me to tell if this really is my problem?

---

### Post by stovicek on 2010-03-27
The Gnome Disk Utility should be able to tell you whether or not the drive is failing. 

System > Administration > Disk Utility

If you don't have it installed, you can get it with:

sudo apt-get install gnome-disk-utility

I've been saved a few times from failing hard drives with it.

---

### Post by jason102 on 2010-03-27
Hi stovicek,

I did what you said, and yes, it's reporting a few bad sectors. I've attached a screenshot showing the report.

So what do I do now? Try out another drive or what? How long do you think I have until this thing dies on me?

---

### Post by RedRat on 2010-03-27
Drives never die when it is convenient, unfortunately. Better to be pro-active than wait for failure. You should not be getting that many errors on the disk. Hard Drives are now fairly inexpensive, well under $100 for 500Gb drives. I think I would spring for a new drive. At least you are getting a warning here.

---

### Post by lotharmat on 2010-03-27
I had this happen to me yesterday - I put it down to the fact I was using Audacity to record some of my terrible guitar playing and even worse singing and had got the input too high and playback was all distorted. Bearing in mind that the speakers are right over the HDD enclosure I was betting that the drive got a bit of a shaking!

It was weird because just before it happened Audigy reported that it was unable to write to the temp file it was trying to write to.

In your case; I'd keep an eye on the reallocated sector count. 1 isn't bad - If it starts to rise - RMA i; I did with a samsung and they just sent me a replacement even though the drive hadn't yet failed.

---

### Post by Whym on 2010-03-27
> **stovicek said:**
> The Gnome Disk Utility should be able to tell you whether or not the drive is failing. 

System > Administration > Disk Utility

If you don't have it installed, you can get it with:

sudo apt-get install gnome-disk-utility

I've been saved a few times from failing hard drives with it.

I tried to get this, but cannot. Any ideas?

```
ubuntu@ubuntu:~$ sudo apt-get install gnome-disk-utility
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-disk-utility
ubuntu@ubuntu:~$ 

```

Thanks in advance.;)

---

### Post by jason102 on 2010-03-27
OK, in this case I'll be getting a new drive then. It's been a year and a half so I guess it wouldn't hurt. Thanks for the heads up - I've never used the Disk Utility program before so now I know! 

I should've pursued this issue earlier... I guess I'm lazy! I've been warned!

---

