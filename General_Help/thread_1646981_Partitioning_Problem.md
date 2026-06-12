---
title: "Partitioning Problem"
date: 2010-12-16
forum: General Help
---

### Post by Inphernal on 2010-12-16
Hi all,
I'm trying to install Ubuntu 10.10 to dual boot with my Win7 installation. I have one HDD, 450GB, it currently looks like this:

/dev/sda
     /sda1 - ntfs - 1.9GB - boot
     /sda2 - ntfs - 140GB
     UNALLOCATED SPACE 80GB
     /sda3 - unknown - 9GB - hidden
     UNALLOCATED SPACE 230GB

My problem here is the partition at /sda3. This seems to be my Win7 recovery partition. I want to move that partition so that I can combine the unallocated space and make a large /home partition and small / partition. I am trying to do this using KDE Partition Manager, but do not get the option to move /sda3. 

Halp?

Thank you

---

### Post by leclerc65 on 2010-12-16
I use gParted live CD for all my partitioning jobs.

---

### Post by dabl on 2010-12-16
You need to use the Win 7 partitioning tool to do that.

Then (using GParted) you'll need to make the fourth partition "extended" type, then you can make logical partitions for the OS and swap within the extended partition.

---

### Post by Inphernal on 2010-12-16
I will download and burn a GParted Live CD.
How do I use that to do what I'm trying to get done?

> **dabl said:**
> You need to use the Win 7 partitioning tool to do that.

Then (using GParted) you'll need to make the fourth partition "extended"  type, then you can make logical partitions for the OS and swap within  the extended partition.

How do I do that with the Win7 tool, it doesn't show the option to move

---

### Post by dabl on 2010-12-16
First use Win 7's partitioning tool to move the sda3 partition up against the sda2 partition.  Then boot your GParted Live CD and use it to make a fourth partition, type=extended, and then you can make 2 or 3 logical partitions inside that.  Here's guidance:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Inphernal on 2010-12-16
> **dabl said:**
> First use Win 7's partitioning tool to move the sda3 partition up against the sda2 partition.[]("http://www.dedoimedo.com/computers/gparted.html")

How do I do this part, Disk Management doesn't seem to give me this ability

---

### Post by oldfred on 2010-12-16
Post this from a liveCD.

```
sudo fdisk -lu
```

Maybe windows thinks one or more of the unallocated is really a partition?

---

### Post by Inphernal on 2010-12-16
> **oldfred said:**
> Post this from a liveCD.

```
sudo fdisk -lu
```Maybe windows thinks one or more of the unallocated is really a partition?

```
Device      Boot Start           End            Blocks        ID  System
/dev/sda1 *      2048           3074047    1536000     27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2         3074048     295555071 146240512 7    HPFS/NTFS
/dev/sda3         469635072 488396799 9380864     17   Hidden HPS/NTFS
```

I launched GParted LIVE CD and it shows a ! by sda3 and labels the file system as unknown

---

### Post by Inphernal on 2010-12-16
I made a system repair disc and system image discs when I first set up Win7, could I just delete this partition?

---

### Post by oldfred on 2010-12-16
The repair disk you may use. Do you ever even think you might even want to recover to the image as purchased. If your image disk is good there is no reason to save partition. Some do not let you write a second one anyway.

If shrinking win7 use windows tools to shrink it.

If you right click on the sda3 in gparted, does it show why you have an ! ? It may not let you delete it until the problem is solved.

---

### Post by Inphernal on 2010-12-16
> **oldfred said:**
> The repair disk you may use. Do you ever even think you might even want to recover to the image as purchased. If your image disk is good there is no reason to save partition. Some do not let you write a second one anyway.

If shrinking win7 use windows tools to shrink it.

If you right click on the sda3 in gparted, does it show why you have an ! ? It may not let you delete it until the problem is solved.

Yes, I used the Win7 tools to shrink my Win7 before, creating that unallocated space.
So basically, as long as I have my recovery disk I will be ok, especially with the system image?

gparted says it may not recognize the file system

---

