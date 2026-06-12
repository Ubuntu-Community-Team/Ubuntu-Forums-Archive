---
title: "i know this will be hard to ask"
date: 2009-07-11
forum: General Help
---

### Post by codered1444 on 2009-07-11
i had ubuntu 9.04 on this comp but my brother hated it (his comp) so i wiped the disk with active killdisk and tried to load the working windows xp cd and at the bottom when it said loading windows i got the notorius blue screen about the new hardware crap

---

### Post by lisati on 2009-07-11
That's why many of us use Ubuntu and/or other Linux distributions......

Was it an original Windows disk which you bought or that came with the machine? You need to be careful with xp disks that you get from "don't ask too many questions"...... too many risks of legal hassles and/or malware.

---

### Post by codered1444 on 2009-07-11
bought

---

### Post by lisati on 2009-07-11
That's ok then.......


p.s. This is a Linux forum......

---

### Post by codered1444 on 2009-07-11
ok
then but i've used it once on this comp and i tried out ubuntu and when i wiped the drive could not load the cd again

---

### Post by CSandman on 2009-07-11
Sounds like you got a recovery disk not a WinBlow$ disk.  It's not linux's fault (and possibly not your fault) that WinBlow$ doesn't like having it's partition size being changed.  You're going to need to find a WinBlow$ disk so that you can use it's repair functionality to setup the disk again, and you'll also need a WinBlow$ forum to ask any other more specific questions.

Good luck.

---

### Post by merlinus on 2009-07-11
You might use gparted to format the hdd as ntfs, and then try installing xp.

---

### Post by codered1444 on 2009-07-11
how do i format it into ntfs while in ubuntu is their a live cd i could use or something

---

### Post by codered1444 on 2009-07-11
i know for a fact its not a recovery disk

---

### Post by codered1444 on 2009-07-11
is there a software which i can boot off cd and format to nfts

---

### Post by moster on 2009-07-11
buddy, your win disk is not good then, or your bios is not setup that boot startup first look on cd and after that on HDD.

There is no matter what kind of filesystem you have. When you eventually do boot from cd, you can/must make in installation ntfs partition to actually install windows.

edit:
That should load even if you do not have hard disk in computer.

---

### Post by itsjareds on 2009-07-11
> **codered1444 said:**
> i know for a fact its not a recovery disk

Is it the Windows install disc? This also acts as the recovery disk because it will give you the option to repair your installation and I'm pretty sure there's a partition formatter in there.

> **codered1444 said:**
> is there a software which i can boot off cd and format to nfts

First try to see if you can format through the Windows install disc, but if not, you should download and burn [GParted Live]("http://gparted.sourceforge.net/download.php") to a CD. If you know how to boot a CD, running GParted should be simple enough to not explain.

---

