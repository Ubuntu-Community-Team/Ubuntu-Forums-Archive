---
title: "How do I shred my External hdd?"
date: 2010-04-26
forum: General Help
---

### Post by rufuslucky on 2010-04-26
I have a pretty simple question. I want to shred my external hdd, Ubuntu is telling me that there are some bad sectors on it, and I want to see if a complete wipe will fix the "bad sectors" before I exercise the warranty. I went and used a live cd to identify the the pathway and the partition manager said it was /dev/sdd1 but...

rufus@rufus-desktop:~$ sudo shred -fvz -n1 /dev/sdd1
shred: /dev/sdd1: failed to open for writing: No such file or directory
rufus@rufus-desktop:~$ 

How do I find out what that drive is so I can erase it???

---

### Post by Penguin Guy on 2010-04-26
Use [FONT="Courier New"]fdisk -l[/FONT] to list all your devices. As for shredding it, I don't see the need - why not just delete everything from it normally using GParted or Palimsest?
Also, to delete the HDD you would use [FONT="Courier New"]/dev/sdd[/FONT] not [FONT="Courier New"]/dev/sdd1[/FONT] (which only deletes the first partition).

---

### Post by Dayofswords on 2010-04-26
you could type in```
df
```
you could look for info that matches what your external drive has and do that one. but defiantly check for sure.
(i'm still new though, look for more posts)

---

### Post by rufuslucky on 2010-04-26
Thanks df worked. 


As for shredding it, I don't see the need - why not just delete everything from it normally?

I want to shred it for two reasons. 1: I am wondering if the bad sectors correspond to something that WD put on there for some reason or another. 
2: If I do have to exercise my warranty and send the thing back to WD I'd prefer it if they didn't have the option of browsing through my my movie collection.

Also thanks for the tip about sdd1 vs sdd

---

### Post by iponeverything on 2010-04-26
You can use dd to overwrite the entire device with zeros.

your if would be if=/dev/zero and of would be something like of=/dev/sdx. 

I intentionally didn't put something that could just be pasted and in ran. Way to many people destroy their data because they stumble on dd and other commands and run them, without understanding what they are doing and nuke an important drive in their system.  

Even people that do understand make typo's and destroy data, so just make sure your very sure before you hit "return"

---

### Post by Lampi on 2010-04-26
use shred:
```
shred -vzn0 /dev/shreddingdeviceorpartition
```
needless to say you backup valuable data first before doing so

---

### Post by Grenage on 2010-04-26
While the shred angle has been covered, I'd recommend returning the drive anyhow.  A drive with bad sectors will, more often than not, continue creating bad sectors.

---

### Post by rufuslucky on 2010-04-28
All right shredded, and a Tb only took what two days...

Amy way I have run into a new problem, The newly wiped disk is no longer "showing up"  

rufus@rufus-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rufus@rufus-desktop:~$

you can see it here it's the WD, but I can't find it under my computer and it's not mounting automatically. I'm guessing it's a formating or driver issue, but I'm not sure where to begin any suggestions.

---

### Post by rufuslucky on 2010-04-28
> **Grenage said:**
> While the shred angle has been covered, I'd recommend returning the drive anyhow.  A drive with bad sectors will, more often than not, continue creating bad sectors.

Not a bad idea, I think I would like to put ntfs back on it before I do so. Moreover, I want contact WD a see what they suggest for testing for "bad sectors." I'd like to be sure the warranty covers my problem before I ship it out.

---

### Post by Grenage on 2010-04-28
Part of the Seagate (who now run WD) RMA process covers use of their tools, including a code for those who can't run the utility.  Their returns system is outstanding.

---

### Post by dcstar on 2010-04-28
People obviously have no idea how hard drives work.

Writing anything at the OS level will not do anything to bad blocks - except maybe wipe out the entries in whatever OS partition that was told to avoid them.

There has not been any sort of "formatting" available for hard drives for decades now, and most modern drives will try to remap bad blocks themselves to the spare allocation area reserved for such things - once that is full, or the problem is more than a few blocks then, as they say, all bets are off.

Disks that comply to the ATA standard have an in-built Secure Erase function that may try to even write to blocks that the drive knows are bad, but there are no guarantees either with that.

You need to run a thorough SMART test on the drive and see if that can remap the blocks, if that cannot then you either have a new paperweight or something to swap if it is under warranty.

---

### Post by Grenage on 2010-04-28
With modern drives, I don't think SMART tests are required.  After successive failed read attempts, the sectors should be marked as bad.

---

### Post by dcstar on 2010-04-28
> **Grenage said:**
> With modern drives, I don't think SMART tests are required.  After successive failed read attempts, the sectors should be marked as bad.

Yes, it should happen basically transparently, but a thorough SMART test will tell you how many problems the drive has and give you some ammo when trying to get it replaced.

---

