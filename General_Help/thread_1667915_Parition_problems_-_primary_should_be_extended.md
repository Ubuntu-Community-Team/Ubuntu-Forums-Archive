---
title: "Parition problems - primary should be extended?"
date: 2011-01-15
forum: General Help
---

### Post by Gibbs on 2011-01-15
Hey,

In a bit of a situation with my HD partitions. Originally I had 4 partitions but in an attempt to reorganise things it messed up. 

I deleted the first partition which was just space and increased the second extended partition to create three partitions instead of four. Something messed up along the way so I'm using testdisk from a Live CD to try and sort it out (hope im making sense, very tired).

With testdisk I've managed to resolve nothing showing up to a degree using:
```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1 37951 254 62  609698816
L Linux Swap           37952 242 51 39197 207 34   19998704
P HPFS - NTFS          39197 207 51 65306  38 12  419430400
D Linux                65306  38 13 121601  57 56  904380416


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue

```

Here's a screenshot from gparted:[http://img412.imageshack.us/img412/3093/screenshotdevsdagpartedu.png](http://img412.imageshack.us/img412/3093/screenshotdevsdagpartedu.png)

The problem; sda1 (which is Ubuntu) is meant to be under an extended partition alongside the swap partition. I cant seem to make anything extended in testdisk though so I'm out of ideas.

Is there a way or different method to get sda1 into the extended partition?

Cheers

---

### Post by srs5694 on 2011-01-15
There's little or no advantage to turning /dev/sda1 into a logical partition, so I can't recommend you try to do so. It *is* possible, but I don't know of any utility that will do it directly, so you'd need to edit sfdisk output and re-input it or use tools that aren't really designed for the task. If you've got a specific reason why you need to change it to a logical partition, please post it.

Your free space is outside of the extended partition, so to use it you'll need to do one of four things:


[list]
[*]Create a primary partition (you'll be limited to one) directly in the free space
[*]Move /dev/sda3 to the left and expand the extended partition. If /dev/sda3 is bootable, you should move/resize it with Windows tools, not with GParted.
[*]Delete /dev/sda5 and /dev/sda2, expand /dev/sda1 (or /dev/sda3, with the above caveats) to cover the freed space this creates, create a new extended partition after /dev/sda3 in the free space in that area, create a new /dev/sda5 swap space in the new extended partition, and create any additional partition(s) you want in the free space within the extended partition. Despite its complexity, this is actually safer than the previous option, at least if you expand /dev/sda1 rather than /dev/sda3, since moving partitions or expanding them to the left is risky; expanding partitions to the right is much safer.
[*]Convert the disk from the Master Boot Record (MBR) format is clearly uses to the newer GUID Partition Table (GPT) format. This can be done without trashing data in partitions with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program, but you'll need to re-install your boot loader. Also, Windows can't boot from a GPT disk on a BIOS-based computer, so if /dev/sda3 is a bootable Windows installation, I advise against this option. If that's an NTFS data partition, though, and if you use Windows Vista or 7, a GPT conversion should be fine. Since GPT doesn't use the primary/extended/logical distinction and it supports up to 128 partition (by default), using GPT simplifies things greatly.
[/list]

---

### Post by Gibbs on 2011-01-16
thanks for the suggestions, ive got it pretty much sorted now.

another thing ive noticed when resizing an

d creating partitions is that they leave an "unallocated" partition at the end which is around 10mib each. is that normal behaviour?  it doesnt seem to effect the 4 partition limitations but curious.

---

### Post by srs5694 on 2011-01-16
Anything marked "unallocated" is by definition *not* a partition; that's free space in-between partitions.

When using GParted, 10 MiB between partitions is excessive, and I don't know why you'd be seeing that, but it does no real harm, aside from preventing you from accessing a few tens of megabytes of disk space. Depending on the GParted version and how the disk was initially partitioned, though, you might see *1* MiB (not 10) unallocated between partitions. This has to do with the way partitions used to be aligned (on fictitious "cylinder" boundaries) vs. the preferred way of aligning them today (on 1 MiB boundaries). The latest versions of GParted tend to ignore small gaps like this, but some versions show them.

In any event, unless the gaps are really big, I wouldn't mess with them; moving and resizing partitions is inherently dangerous, so attempting to use that space requires dangerous operations, unless you happen to want to move or resize partitions for other reasons.

---

