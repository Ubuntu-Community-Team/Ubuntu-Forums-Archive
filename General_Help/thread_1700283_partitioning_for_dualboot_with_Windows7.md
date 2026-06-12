---
title: "partitioning for dualboot with Windows7"
date: 2011-03-04
forum: General Help
---

### Post by tlroche on 2011-03-04
Your suggestions regarding the following project are appreciated:

I've got a new box (i.e. I can blow away everything on it) with

[LIST]
[*]CPU=Atom 330
[*]nVidia GeForce 9400M
[*]4 GB RAM
[*]single drive, single partition=250 GB
[*]Ubuntu 10.10 installed
[/LIST]

The box will primarily be used for ubuntu, but my GF also wants to stream Netflix on it. (I have not been able to sell her on the [Amazon Instant Video]("http://en.wikipedia.org/wiki/Amazon_Instant_Video")--yet, anyway.)

Since Netflix doesn't run on Linux, I need to install a Windows or OSX. I have media for w7 and wXP. I'm planning to install w7 on it, just because that's newer. Is there a reason to install wXP instead for this usecase?

Given w7, I can choose to dualboot or virtualize. I'm told the Atom doesn't virtualize well, so I'm planning to dualboot.

I'm told that, when dualbooting linux and windows, one wants to partition first, then install windows, then install linux, so I'm planning to do that.

The question is then, how to partition for this? My plan is currently to make 5 partitions: 2 primary partitions (one for each OS) and 1 extended partition (to hold linux swap and the homes for w7 and ubuntu)

```
primary partitions:
system (c:) for w7   = 20 GB
root for ubuntu      = 20 GB
extended partition:
swap for ubuntu      =  4 GB
home/apps/swap for W7= 16 GB
home for ubuntu      =190 GB (or whatever's left on the disk)
```

Does that seem reasonable, or is there a better way to do this?

---

### Post by wiggly81 on 2011-03-04
have you considered installing virtualbox and adding windows as a virtual machine, this way you don't have to change partitions and your GF can still use windows

---

### Post by tlroche on 2011-03-04
> **tlroche said:**
> I can choose to dualboot or virtualize. I'm told the Atom doesn't virtualize well, so I'm planning to dualboot.

> **wiggly81 said:**
> have you considered installing virtualbox and adding windows as a virtual machine

No, because I'm told the Atom doesn't virtualize well. Is this not correct?

> **wiggly81 said:**
> this way you don't have to change partitions

Even if I did not dualboot, I would still repartition, in order to have separate root, home, and swap partitions.

---

### Post by Dans564 on 2011-03-04
If u install w7 first, then pop in the ubuntu dvd or cd one of the partitioning choices should be install along side other os.  Obviously choose that option.  Move the slider to determine how mang GB's each os gets and click install.  :D:D:D

Easy as pie. 

hope this helps!!

---

### Post by flyerbrooks on 2011-03-05
Agree with Dans564
Windows first and linux second makes for a pain free and easy experience normally. Just take time to read your partition options through first.
Have fun!

---

### Post by rishabhpadita on 2011-03-05
its good to install Linux aft w7 as grub understands w7 but bootloader of w7 does not get ne other os

---

### Post by Mark Phelps on 2011-03-05
If you install Win7, do NOT, repeat NOT, just stick in the CD and allow the Ubuntu installer to shrink the Win7 OS to make room for Ubuntu.  Doing that is asking for trouble, and if you encounter that, you then run the risk of rendering your Win7 unbootable.

If you have, or can use, a CD drive with your PC, BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You might need this later to repair the Win7 boot loader or other booting problems.

Also, when in Win7 take a look at your existing partitions in the Disk Management utility. If you already have four partitions, you can not just create a new one for Ubuntu because doing that will force your Win7 install into Dynamic Disks -- something you do NOT want to do.

If you have less than four partitions, then go ahead and use Disk Management to shrink the Win7 OS partition, leaving room for Ubuntu.  Don't format that space in Win7.  Let the Ubuntu installer format it.

But be very careful when formatting in the installer.  Canonical removed the "Use largest free space" option, and unless you're very careful, you will format your Win7 install by mistake and erase it.

---

