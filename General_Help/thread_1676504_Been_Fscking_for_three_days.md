---
title: "Been Fscking for three days"
date: 2011-01-27
forum: General Help
---

### Post by Uruz on 2011-01-27
Okay, so I have a 500GB hard drive divided into three partitions (Ubuntu, Windows XP, Storage). The two OS's are 107GB each and the remaining space is devoted to the storage partition (which is ext4)

I had done a similar set up on a previous hard drive, but with ext3 formatting on the Linux and Storage partitions. This time, however, the program I was using for ext3 support would not work with ext4 (I assumed this would fall under the category of "backwards compatibility"). I got a new program and messed with its settings until it worked.

At first only my Linux partition showed up, not the Storage partition. More tinkering got that working too, but it was buggy. Folders would not contain their proper contents (often, all folders except for my Dropbox would contain two folders named "dropbox," neither of which could be opened) Also, if any significant amount of writing was done to the partition, I would have to run Fsck for it to work in Ubuntu again. Each time Fsck would fix something different.

This time, it's been running for three days. It's allocating unallocated blocks one at a time (I used they -y command). All of the blocks are in one section (I forget the number).

My questions are: What is this? Is there some alternative? Is there a safe way to end this (I've got to shut it down tomorrow to take back home with me)?

Definitely I'm going to switch it back to ext3.

Thanks for any help,
Uruz

---

### Post by cherva on 2011-01-27
The easiest way is to switch back to ext3 or you can make your storage NTFS so it will work in windows and ubuntu can read/write to ntfs partitions so there will be no need for another program to save somethin on the storage partitions on both windows and linux sides :)

---

### Post by Mark Phelps on 2011-01-27
My guess would be that "the program" you are using is corrupting the Ext4 filesystem.

Would second the suggestion to use NTFS for shared data storage -- unless you need Linux permissions in place.

In that case, you will need to STOP using "the program" -- and see if the filesystem corruption then stops as well.

---

### Post by Uruz on 2011-01-27
Well, my biggest problem with NTFS is getting Ubuntu to let me own, read and write to it. Also I had a problem with Windows installing vital system files to the partition and then breaking when I wiped it.

My main question is just about what this Fsck is doing. I didn't expect it to go this long...

---

### Post by Grenage on 2011-01-27
'Ownership' is entirely dependant on how it was mounted, and the flags used.  As for Windows installing vital files on an extra partition, that just doesn't happen unless it's been designated a system directly.

I'm not sure *how* that would be accomplished accidentally.

---

### Post by Uruz on 2011-01-27
> **Grenage said:**
> 'Ownership' is entirely dependant on how it was mounted, and the flags used.  As for Windows installing vital files on an extra partition, that just doesn't happen unless it's been designated a system directly.

I'm not sure *how* that would be accomplished accidentally.

My brother theorizes that it may have been caused by the NTFS storage partition (which had not been completely reformatted since its days as a Windows Partition) containing some windows root-files which the windows assumed belonged to it and therefore used them rather than make new ones on the partition I had meant for it to install to.

Anyway, is there a problem with my drive? Am I going to lose data? What's going on?

---

### Post by Grenage on 2011-01-27
> **Uruz said:**
> Anyway, is there a problem with my drive? Am I going to lose data? What's going on?

To be honest, it sounds wrecked.  The fact that things were being fixed en each check, and that the latest check is never ending - there are serious issues.

I would guess that this unnamed program has damaged the data on the partition, or that the drive is failing.  Considering that the other partitions seem fine, the former seems likely.

---

