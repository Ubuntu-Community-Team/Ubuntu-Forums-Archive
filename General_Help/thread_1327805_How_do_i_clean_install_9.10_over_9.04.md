---
title: "How do i clean install 9.10 over 9.04?"
date: 2009-11-15
forum: General Help
---

### Post by eulnuj on 2009-11-15
So when I get to partitions step, I click manual advance to specify installation, but there is no option of freespace, or option to write over the existing 9.04 partitions.

what to do?

---

### Post by XubuRoxMySox on 2009-11-15
> **eulnuj said:**
> So when I get to partitions step, I click manual advance to specify installation, but there is no option of freespace, or option to write over the existing 9.04 partitions.

what to do?

Assuming two things:

1.) That you have backed up your important stuff, and

2.) That you want to replace your old 9.04 with 9.10,

Select your old 9.04 partition and choose **Edit**.

(On my 80-gig hard drive, I designate 10-15 gigs for "/", 1 gig for swap - which is double my 512 RAM - and the rest is "/home".

The first partition, "/" is where your new Karmic system should go. You can choose either ext4 or ext 3 as the file system (ext4 is the default) and check the box that says "Format this partition."

If you have a previous "/home" partition that you want to keep, un-check the little box that says "Format this partition." This should prevent those files (your documents, photos, favorites, e-mail settings, etc) from being lost (back them up anyway before you start just in case).

Your Karmic will install to the position designated as "/" when you select "Format."

I hope this helps,
Robin

---

### Post by Manyette on 2009-11-15
Right click on existing partitions, then select delete until all are gone!

---

### Post by hansdown on 2009-11-15
HI eulnuj.

Click "erase and use entire disk".

---

### Post by alexfish on 2009-11-15
> **eulnuj said:**
> So when I get to partitions step, I click manual advance to specify installation, but there is no option of freespace, or option to write over the existing 9.04 partitions.

what to do?
firstly think about over writing 9.04    9.10 has some changes regarding the kernel
if you have a spare harddrive / i use an external usb drive for testbeding /  then do a clean install of 9.10 disconnecting any other harddrives internaly is my prefered option as there are issues regarding grub and ext4 / and any other os's you may want to keep on the drive /then reconnect the drives and select the boot drive from the bios never cared for grub  lilo would be my prefered option 

however when in the partition bits just select USE WHOLE DISK /option ext4 
or if you have other os on the disk you want to keep reformat the partition you want to overwrite you can use ext 3 that would be my choice but its its upto you which to chose


the formating can be done with the livecd     the reason that i do it this way is that if one os is working with out problems then at least there is something to fall back on

---

### Post by ranch hand on 2009-11-15
Before you follow any of this I hope that you realize that all the advise is good unless you have more than 9.04 on that drive.

I think it would be nice if you would post the results of;
```

sudo sfdisk -l

```

---

### Post by hansdown on 2009-11-15
> **ranch hand said:**
> Before you follow any of this I hope that you realize that all the advise is good unless you have more than 9.04 on that drive.

I think it would be nice if you would post the results of;
```

sudo sfdisk -l

```

Good point ranch hand.

---

### Post by eulnuj on 2009-11-15
> **ranch hand said:**
> Before you follow any of this I hope that you realize that all the advise is good unless you have more than 9.04 on that drive.

I think it would be nice if you would post the results of;
```

sudo sfdisk -l

```

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    191-    192-   1536000   27  Unknown
/dev/sda2   *    191+  21710-  21519- 172851200    7  HPFS/NTFS
/dev/sda3      21711   24320    2610   20964825    5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      21711+  21958     248-   1992028+  82  Linux swap / Solaris
/dev/sda6      21959+  23825    1867-  14996646   83  Linux
/dev/sda7      23826+  24320     495-   3976056   83  Linux


Here ya go

---

### Post by ranch hand on 2009-11-16
Ok, you have a setup that looks like it works so lets do what we should have done before and post the results of this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

This will actually tell us everything we need to know about your setup to put it right where you want it.

---

