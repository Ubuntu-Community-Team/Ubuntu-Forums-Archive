---
title: "Shrinking an extended partition"
date: 2011-04-14
forum: General Help
---

### Post by Dr. Quack on 2011-04-14
Hey everyone!

I recently decided to resize a partition on my HDD (partition on which Ubuntu was previously installed). This was in order to remove Ubuntu from one of my HDD. I got rid of the Grub loader by booting on my windows system recovery disk and using Bootrec.exe/FixMbr and my computer now boots directly into windows. I then deleted the Ubuntu partition.

To get to the heart of the problem, I am trying to move the free space that is in the extended partition out and merge it with C. I tried doing this with my Gparted liveCD but it didn't work. I didnt have anything to save the error message onto, but I will try the process again when I get home and save the error onto my external drive so that I can post it here. 

I would greatly appreciate any help I could get with this problem. Resources to read would be great if you don't have time for this.

Thank you!
Dr. Quack

---

### Post by seawolf167 on 2011-04-14
Here is a [how-to ]("http://www.sevenforums.com/tutorials/2670-partition-volume-extend.html")on resizing NTFS partitions using the Windows partition editor (I prefer the Windows partition editor for NTFS volumes)

---

### Post by Dr. Quack on 2011-04-15
Hi,

Thanks for your answer. Unfortunately I don't think it is a simple as that. To my understanding, it is only possible to create 4 partitions in NTFS, and so the 4th partition created is called an 'extended partition'. This extended partition then lets you subdivide it into other partitions, thus letting you create more of them.

What I am trying to do is move the 'Free space' out of the extended partition, in order to merge it with C:.

Should I try merging the free space with D: and then cutting it out again, or would I just end up where I am now again?

---

### Post by seawolf167 on 2011-04-15
When you resize the extended partition, the free space will become unallocated. Yes, you could *not* create a new primary partition with it since as you said, there is a primary partition limit, but resizing an existing primary partition is acceptable, you just have to ensure that the free space is aligned at the beginning/end of the partition boundaries.

---

### Post by Dr. Quack on 2011-04-15
Ok. That means that I'll have to try and merge the free space with D: and then cut a chunk off, since there seems to be no way to shrink the extended partition in windows and gparted doesn't want to do it either. If that doesn't work I'll just delete the whole extended and restore D:

---

### Post by seawolf167 on 2011-04-15
GParted generally doesn't like NTFS partitions too much, you'll want to get

```
sudo apt-get install ntfsprogs
```

to get full NTFS compatibility. This is why I suggested using the Windows partition editor after you resize the *nix filesystem as (IMO) it generally works better with NTFS partitions.

You should also have the ability to "move" the partition(s), and you should be able to move it and the unallocated space around so the resizing will work.

---

### Post by techunit on 2011-04-15
It is much simpler than that I believe. You should be able to just boot into the Ubuntu Live CD use Gparted to delete the extended partition. Apply changes and reboot back into windows you should be able to resize the windows C drive with the Windows Disk Management

Sorry to see you go. If you ever get bored remember Wubi is a quick fix. Good Luck.

---

### Post by srs5694 on 2011-04-15
> **Dr. Quack said:**
> Ok. That means that I'll have to try and merge the free space with D: and then cut a chunk off, since there seems to be no way to shrink the extended partition in windows and gparted doesn't want to do it either. If that doesn't work I'll just delete the whole extended and restore D:

Chances are GParted doesn't want to do it because the partition is in use. If there's a key icon next to a partition in the partition list in the bottom part of the GParted window, that's what's going on. If you've booted from a live CD, you should be able to right-click the icon and select an option to unmount the partition.

If that doesn't help, please post a GParted screen shot, a precise description of the steps you're taking, and a verbatim copy of any error messages GParted produces (perhaps another screen shot).

---

