---
title: "Disk Defragmentation"
date: 2011-01-16
forum: General Help
---

### Post by Alan.Brown on 2011-01-16
In Windows it was recommended that disks be defragmented regularly.   Does this need to be done in Linux?   If so, how?  If not, why not?

TIA

Alan

---

### Post by DeMus on 2011-01-16
> **Alan.Brown said:**
> In Windows it was recommended that disks be defragmented regularly.   Does this need to be done in Linux?   If so, how?  If not, why not?

TIA

Alan

No, Linux uses the disk in another way than Windows does. File are written as one block (defragmented by itself) until the disk is getting almost full. Then, and only then, fragmentation can occur.
If you still have enough space left on your disk you have nothing to worry about.

---

### Post by jbrown96 on 2011-01-16
> **DeMus said:**
> No, Linux uses the disk in another way than Windows does. File are written as one block (defragmented by itself) until the disk is getting almost full. Then, and only then, fragmentation can occur.
If you still have enough space left on your disk you have nothing to worry about.

Not true. Fragmentation is a concern with any rotating media. While file systems can mitigate this problem to an extent, fragmentation will degrade performance. There hasn't been good defragmentation tools in Linux at any point, and largely because there's no meaningful way to address the problem, advocates naturally ignore that fragmentation is a problem.

---

### Post by TNT1 on 2011-01-16
I'd suggest do a search here, and on the intwerwebs, look for ext3 and ext4 fragmentation...

---

### Post by Megaptera on 2011-01-16
> **jbrown96 said:**
> Not true. Fragmentation is a concern with any rotating media. While file systems can mitigate this problem to an extent, fragmentation will degrade performance. There hasn't been good defragmentation tools in Linux at any point, and largely because there's no meaningful way to address the problem, advocates naturally ignore that fragmentation is a problem.

So is the Ubuntu Community info wrong then?
Quote "Another common Windows practice that is not needed in Unix is defragmenting the hard drive. When NTFS and FAT write files to the hard drive, they don't always keep pieces (known as blocks) of files together. Therefore, to maintain the performance of the computer, the hard drive needs to be "defragged" every once in a while. This is unnecessary on Unix File systems due to the way it was designed. When ext3 was developed, it was coded so that it would keep blocks of files together or at least near each other." 
From: [https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by HermanAB on 2011-01-16
Howdy, fragmentation was an issue in the days of FAT and slow disks. 

These days, defragmentation is mostly a waste of time, even on Windows with NTFS.

---

### Post by DeMus on 2011-01-16
I found this on: [http://www.ehow.com/how_4473590_defrag-linux.html]("http://www.ehow.com/how_4473590_defrag-linux.html")

A common question from new Linux users is "How do you defrag your hard drive?" The short answer is that you probably don’t have to. The file system on Linux and other UNIX (and UNIX-like) operating systems is organized and stored more efficiently than the one on a Windows PC. On Windows, PC users will not notice a performance dropoff until fragmentation hits 20 percent or more, which is rare; on a multi-user, multi-tasking, multi-threaded operating system like Linux, the fragmentation of files on the hard disk is usually under 1 percent.

Read more: How to Defrag in Linux | eHow.com [http://www.ehow.com/how_4473590_defrag-linux.html#ixzz1BBSmWF1A](http://www.ehow.com/how_4473590_defrag-linux.html#ixzz1BBSmWF1A)

---

### Post by James78 on 2011-01-16
> **jbrown96 said:**
> Not true. Fragmentation is a concern with any rotating media. While file systems can mitigate this problem to an extent, fragmentation will degrade performance. There hasn't been good defragmentation tools in Linux at any point, and largely because there's no meaningful way to address the problem, advocates naturally ignore that fragmentation is a problem.
As she said, Linux does not require defragmenting as long as you have enough space on your disk. This is due to the way Linux stores files. To help you understand why this is, please read this excellent article, which explains it very well. :)
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Alan.Brown on 2011-01-16
Thanks everyone for all your replies.  I have at least 10GB spare space on both the /root and /home partitions so I will not worry about defragging the disks.

Thanks

Alan

---

### Post by jbrown96 on 2011-01-17
> **DeMus said:**
> I found this on: [http://www.ehow.com/how_4473590_defrag-linux.html]("http://www.ehow.com/how_4473590_defrag-linux.html")

A common question from new Linux users is "How do you defrag your hard drive?" The short answer is that you probably don’t have to. The file system on Linux and other UNIX (and UNIX-like) operating systems is organized and stored more efficiently than the one on a Windows PC. On Windows, PC users will not notice a performance dropoff until fragmentation hits 20 percent or more, which is rare; on a multi-user, multi-tasking, multi-threaded operating system like Linux, the fragmentation of files on the hard disk is usually under 1 percent.

Read more: How to Defrag in Linux | eHow.com [http://www.ehow.com/how_4473590_defrag-linux.html#ixzz1BBSmWF1A](http://www.ehow.com/how_4473590_defrag-linux.html#ixzz1BBSmWF1A)

While Linux file systems historically tended to fragment less than the Windows equivalent, both are pretty good. NTFS is really a very good file system, although it's much maligned by some people because Microsoft doesn't vocally advertise many of its features. 
Fragmentation is a problem with all memory systems. They will fragment over time, given a reasonable write load. Memory fragmentation is a monotonically increasing function. The only way to avoid it is to run some sort of "de-fragmentation" program. There's all sorts of ways to de-fragment memory, depending on its storage characteristics. 
The answer on Linux is fairly complex with several opposing forces. First, Linux largely lacks any de-fragmentation tools for file systems. XFS does have a de-fragmentation utility, but I believe that it is offline-only. Ext4 was supposed to have one, but I don't think that it has been completed yet. Btrfs will have one, but it's really just a neat trick that I'll explain later. 
In Unix, there have been two traditional reasons why de-fragmentation utilities don't exist. 
First, various data storage mechanisms were available. Most Unix servers just serve content, so they are doing reads all the time from disk; since read operations don't increase fragmentation, file "serving" Unix servers didn't need to worry about fragmentation. Other servers were used largely for large downloads and uploads (like FTP). Again, the reads don't cause fragmentation. Large uploads are most likely to cause writes, which are sequential, and they don't cause much fragmentation. Lots of random writes is what causes fragmentation. Databases have traditionally occupied this space because they can handle efficient reads and writes on small amounts of data. One of their "efficient" characteristics is internally managing fragmentation above the VFS layer. Through file system design and storage system schemas, it is possible to maximize performance, which in the long-term includes minimizing fragmentation. 
Second, de-fragmentation isn't feasible in high-availability systems, and Unixes tend to fill these rolls. De-fragmentation operations take a significant amount of CPU time, not to mention the load they put on the storage system. If my system is used 24x7, there's no downtime where I can de-fragment my disks. I'd have to way over provision my storage system to handle all the additional load of de-fragmenting under load. If there's no time to perform de-fragmentation after the data has been written and fragmentation is a problem, then there has to be something to minimize the problem. It turns out that there is, and it happens to be part of the misconceptions about fragmentation on Linux: file systems. There are dozens of currently supported Linux file systems that have all sorts of advantages in different circumstances, some of which are fragmentation characteristics. 
I'd like to outline a few file systems and some of the strengths that they have. Ext4 uses extents to allocate disk space. This really is a performance benefit since it minimizes block lookups. An extent is a range of blocks that are allocated to a single file. However, one side effect is that extents can't be broken up (well, they can but it's inefficient, and the system knows to avoid breaking extents), so files stay more contiguous over their lifetime. It's not foolproof, but it's a mitigating factor. Ext4 and Btrfs are extent-based, which aids in the next trick, but isn't the true source. The VFS layer in Linux does a great job of allocating space in contiguous chunks for an initial write. That means that, given adequate free space, the initial file won't be fragmented. Subsequent writes, particularly random ones, mostly cause fragmentation. The "dirty" trick to de-fragmenting individual files is to simply copy it, delete the original, and rename the copy. For example, ```
cp /home/me/{A,B} ; rm /home/me/A; mv /home/me/{B,A}
``` This works because the copy is (hopefully) allocated in a contiguous section of the disk. The reason that this isn't used is that it doesn't work very well. NILFS is really cool for several reasons. It completely avoids the possibility of fragmentation. However, don't go running to it, because there's all kinds of other trade offs to consider. 
While VFS generally does a good job allocating new files, there is no guarantee that it will. Furthermore, one can't expect that the disk get less fragmented as more files go through the above operation. The real cause of disk fragmentation needs to be fixed at the block layer, which the neat trick can't do. This method also needs lots of free space. The method that Windows uses needs a fixed ratio of free blocks (10-15%) to perform a good de-fragment; whereas the method above doesn't depend on free blocks at all, but the size of files compared to the amount of free, contiguous blocks. This trick works for some files, especially on disks with lots of free space (but disks with lots of free space don't tend to have much fragmentation...). 

Fragmentation shouldn't be much of an issue on a desktop system. I would tend to be more worried on something like a mail server that uses flat files. 
My take on the Ubuntu Community Documentation is that it's very basic. I wouldn't expect it to give a nuanced discussion of disk fragmentation. I imagine that almost everyone that comes across that page wants to know how to de-fragment a disk in Linux because they used to do that in Windows. The short answer is that it's not really possible, but partially because that doesn't look good it isn't said. Combined with the fact that Ubuntu doesn't use anything as terrible as a FAT file system, de-fragmentation isn't much of an issue. 

Fragmentation is a fact of life for any system that must allocate and reclaim scarce resources. There's no way around it. De-fragmentation operations tend to be very computationally difficult and put tremendous stress on the underlying resources. 

I think it's important to look at the lineage of Unix and Windows. Unixes were developed in high-availability systems where system time was expensive and scarce, so de-fragmentation operations weren't possible. Instead of "fixing" a fragmented system, the Unix philosophy is to design around it, so it doesn't become an issue. That's not totally possible, so designers try to minimize fragmentation as much as possible. The systems had to be available all the time; there's no downtime for de-fragmenting. On the other hand, Windows, especially the fragment-prone pre-NT versions, was designed for personal or corporate-desktop use. There's lots of downtime in this environment. The computers won't be used more than eight hours in most situations, so de-fragmentation can take place at night or whenever the computer isn't in use. Microsoft got to use a terrible file system, FAT, because they could mitigate the effects of fragmentation using de-fragmentation. 
I like elegant designs, so I like the Unix approach more, but it's likely that Windows 7 is the least prone system to fragmentation. Current versions of NTFS are superb at preventing fragmentation, and Microsoft has de-fragmentation tools that automatically run when the system is idle. 

In the end, disk fragmentation on Linux shouldn't be a problem for almost all desktop Linux users.

---

### Post by bodhi.zazen on 2011-01-17
Fragmentation occurs with all file systems.

The question is not if fragmentation happens or not, but if fragmentation is severe enough to cause performance problems.

From what I have read, it takes at least 20 % fragmentation to affect performance and I have never seen a linux file system with more then 5% fragmentation tops, typically fragmentation is 1 % or so.

See this post:

[https://forums.gentoo.org/viewtopic-p-3111409.html](https://forums.gentoo.org/viewtopic-p-3111409.html)

So yes, Linux file systems can fragment, but not typically to the point where they affect performance and thus you do not need defragmentation tools.

The only exception to this would be if your partition is full, and then the problem would be space and not necessarily fragmentation.

---

### Post by bodhi.zazen on 2011-01-18
This is what I get for fragmentation on my file systems, both have been in use for over a year, never defragmented.

root ( / ) : 0.576198508662684% non contiguous files, 1.00662904166601 average fragments

My data partition, which has a number of multimedia files and other interesting things such as iso:

/data :

0.408618127786033% non contiguous files, 1.11552748885587 average fragments.

So fragmentation is about 1% as advertised. 

So again, fragmentation happens, but 1% is insufficient to cause a performance hit, IMHO, and I am not loosing any sleep over it any time soon.

---

### Post by James78 on 2011-01-18
> **bodhi.zazen said:**
> [B]Fragmentation occurs with all file systems.

The question is not if fragmentation happens or not, but if fragmentation is severe enough to cause performance problems.[/B]

From what I have read, it takes at least 20 % fragmentation to affect performance and I have never seen a linux file system with more then 5% fragmentation tops, typically fragmentation is 1 % or so.

See this post:

[https://forums.gentoo.org/viewtopic-p-3111409.html](https://forums.gentoo.org/viewtopic-p-3111409.html)

So yes, Linux file systems can fragment, but not typically to the point where they affect performance and thus you do not need defragmentation tools.

The only exception to this would be if your partition is full, and then the problem would be space and not necessarily fragmentation.
Precisely, definitely the entire idea conveyed in this thread. ;) It's pretty nice how the filesystem was designed. Since how it writes to the disk, most files are accessible in an average amount of time, no jumping all over the disk all the time. And to put even more on a good thing, it doesn't typically fragment with how it's designed. :)
> **bodhi.zazen said:**
> This is what I get for fragmentation on my file systems, both have been in use for over a year, never defragmented.

root ( / ) : 0.576198508662684% non contiguous files, 1.00662904166601 average fragments

My data partition, which has a number of multimedia files and other interesting things such as iso:

/data :

0.408618127786033% non contiguous files, 1.11552748885587 average fragments.

So fragmentation is about 1% as advertised. 

**So again, fragmentation happens, but 1% is insufficient to cause a performance hit, IMHO, and I am not loosing any sleep over it any time soon.**
Lol ya.

---

### Post by jbrown96 on 2011-01-18
> **James78 said:**
> Precisely, definitely the entire idea conveyed in this thread. ;) It's pretty nice how the filesystem was designed. Since how it writes to the disk, most files are accessible in an average amount of time, no jumping all over the disk all the time. And to put even more on a good thing, it doesn't typically fragment with how it's designed. :)

Lol ya.

I'm not even sure what you are trying to say here. It's a tautology to say that of all the files on your system "most files are accessible in an average amount of time." If you take all of something you have, then the average of them is the average of them. 
VFS and the file systems attempt to make contiguous allocations, but the results are very dependent on use patterns. 
For example, the next hot thing in Linux file systems is Btrfs. Like all COW file systems, they tend to have poor fragmentation. Btrfs will fragment more than other file systems.

---

### Post by James78 on 2011-01-18
> **jbrown96 said:**
> I'm not even sure what you are trying to say here. It's a tautology to say that of all the files on your system "most files are accessible in an average amount of time." If you take all of something you have, then the average of them is the average of them. 
VFS and the file systems attempt to make contiguous allocations, but the results are very dependent on use patterns. 
For example, the next hot thing in Linux file systems is Btrfs. Like all COW file systems, they tend to have poor fragmentation. Btrfs will fragment more than other file systems.
The average I refer to is the fact that Linux generally writes the data to the middle of the disk, rather than on the sides as NTFS does. This provides an average read/write on most things, where NTFS could be jumping all over (due to the easy fragmentation because of how it writes)

---

### Post by psusi on 2011-01-18
> **HermanAB said:**
> Howdy, fragmentation was an issue in the days of FAT and slow disks. 

These days, defragmentation is mostly a waste of time, even on Windows with NTFS.

Wrong.  It is still quite an issue with Windows and NTFS, the only thing that has changed is that Windows automatically runs a defrag when the screen saver is going.

> **jbrown96 said:**
> While Linux file systems historically tended to fragment less than the Windows equivalent, both are pretty good. NTFS is really a very good file system, although it's much maligned by some people because Microsoft doesn't vocally advertise many of its features. 

It is a decent enough FS, but the Windows NTFS *driver* implementation is retarded, and commonly results in files with many hundreds or thousands of fragments, thus requiring frequent cleanup.

> **jbrown96 said:**
> Fragmentation is a problem with all memory systems. They will fragment over time, given a reasonable write load. Memory fragmentation is a monotonically increasing function. The only way to avoid it is to run some sort of "de-fragmentation" program.

No, it is not.  If you delete a badly fragmented file, then you have reduced fragmentation.  While the only way to *reduce* fragmentation that has already occurred is to run a defrag program, it can be *avoided* with good allocation algorithms.

> **jbrown96 said:**
> First, Linux largely lacks any de-fragmentation tools for file systems.

It lacks them because they are not needed.  There was a defrag utility for ext2 but it was abandoned over 10 years ago because the kernel got good enough at resisting fragmentation in the first place that it was rendered unnecessary.  I dug it up and resurrected it for fun at launchpad.net/e2defrag.

> **jbrown96 said:**
> Ext4 uses extents to allocate disk space. This really is a performance benefit since it minimizes block lookups. An extent is a range of blocks that are allocated to a single file. However, one side effect is that extents can't be broken up (well, they can but it's inefficient, and the system knows to avoid breaking extents), so files stay more contiguous over their lifetime.

Extents do not affect fragmentation one way or the other.  It is another ext4 feature called delayed allocation that helps with fragmentation.  Rather than allocate blocks as the file is written it waits, hopefully until you finish writing the file and close it, then it knows the full file size so it can go allocate an extent large enough to hold it all.

> **jbrown96 said:**
> Combined with the fact that Ubuntu doesn't use anything as terrible as a FAT file system, de-fragmentation isn't much of an issue. 

There is nothing about FAT that makes it inherently bad for fragmentation.  It is all about the allocation algorithm the flesystem driver uses.  The same algorithms that ext[234] use to resist fragmentation could be applied to FAT.

---

### Post by jbrown96 on 2011-01-18
> **psusi said:**
> Wrong.  It is still quite an issue with Windows and NTFS, the only thing that has changed is that Windows automatically runs a defrag when the screen saver is going.
Please provide a citation for this because it doesn't match any experience I've had with Windows in over a decade. 


> 
It is a decent enough FS, but the Windows NTFS *driver* implementation is retarded, and commonly results in files with many hundreds or thousands of fragments, thus requiring frequent cleanup.
NTFS has evolved tremendously over its lifetime, and is dramatically improved now. Defrag isn't needed on NTFS any more than other file systems. 


> 
No, it is not.  If you delete a badly fragmented file, then you have reduced fragmentation.  While the only way to *reduce* fragmentation that has already occurred is to run a defrag program, it can be *avoided* with good allocation algorithms.Fragmentation cannot be avoided. It can be mitigated, through allocation and defrag operations. There is no way for an allocation alogrithm to avoid fragmentation on a disk that isn't mostly empty. 


> 
It lacks them because they are not needed.  There was a defrag utility for ext2 but it was abandoned over 10 years ago because the kernel got good enough at resisting fragmentation in the first place that it was rendered unnecessary.  I dug it up and resurrected it for fun at launchpad.net/e2defrag.
Please explain how the VFS layer has any control over allocations on a mostly full disk. VFS doesn't do on-the-fly reorganization of blocks, so in any situation where a new file needs more blocks than can be contiguously allocated, there will be fragmentation, and it will not be fixed without copying or a defrag operation. 


> 
Extents do not affect fragmentation one way or the other.  It is another ext4 feature called delayed allocation that helps with fragmentation.  Rather than allocate blocks as the file is written it waits, hopefully until you finish writing the file and close it, then it knows the full file size so it can go allocate an extent large enough to hold it all.
Correct. Extents don't directly reduce the chance of fragmentation, but understanding extents helps people understand fragmentation. 


> 
There is nothing about FAT that makes it inherently bad for fragmentation.  It is all about the allocation algorithm the flesystem driver uses.  The same algorithms that ext[234] use to resist fragmentation could be applied to FAT.
Partially correct. A FAT doesn't necessarily cause fragmentation, but to have good performance it's necessary to accept fragmentation. To allocate blocks from a FAT, you must scan a linear table to find free space, which uses a lot of resources. To avoid rescanning (in the case of a mis-allocation) the FAT, the best option is to use blocks that may not necessarily be contiguous. Repeatedly scanning a FAT is the only practical way to allocate the largest chunks available (again assuming we're outside the simple case of empty drives). The performance penalty, especially on large disks, is unacceptable, so we typically allow fragmentation now to speed the initial write. Subsequent reads and writes can greatly suffer, which is why FAT is always inappropriate if alternatives are available.

---

### Post by psusi on 2011-01-18
> **jbrown96 said:**
> Please provide a citation for this because it doesn't match any experience I've had with Windows in over a decade. 

I may be wrong on this.  I had assumed that all the hd activity that usually happens when the screen saver kicks in was a defrag.  I thought I had read about that somewhere at some point years ago too, but I guess it isn't since I just checked this windows machine and it's quite fragmented.  I may be thinking of diskkeeper or another third party program.

> **jbrown96 said:**
> NTFS has evolved tremendously over its lifetime, and is dramatically improved now. Defrag isn't needed on NTFS any more than other file systems. 

Is this something new in Windows 7?  I should be getting a new machine at work soon with that so I'll have to check it out.

> **jbrown96 said:**
> Fragmentation cannot be avoided. It can be mitigated, through allocation and defrag operations. There is no way for an allocation alogrithm to avoid fragmentation on a disk that isn't mostly empty. 

There are a number of ways to avoid it that work just fine on a disk with only 20% free space.  Some of the techniques include delayed allocation and preallocation.

> **jbrown96 said:**
> Please explain how the VFS layer has any control over allocations on a mostly full disk. VFS doesn't do on-the-fly reorganization of blocks, so in any situation where a new file needs more blocks than can be contiguously allocated, there will be fragmentation, and it will not be fixed without copying or a defrag operation. 

I never said it did.  It is the filesystem driver that does that.  You are the one who seems to be attributing more functionality to the VFS layer than it has.

> **jbrown96 said:**
> Partially correct. A FAT doesn't necessarily cause fragmentation, but to have good performance it's necessary to accept fragmentation. To allocate blocks from a FAT, you must scan a linear table to find free space, which uses a lot of resources.

There is no reason that the FAT filesystem driver could not keep an in memory block allocation bitmap to speed up allocation.

> **jbrown96 said:**
> To avoid rescanning (in the case of a mis-allocation) the FAT, the best option is to use blocks that may not necessarily be contiguous. Repeatedly scanning a FAT is the only practical way to allocate the largest chunks available (again assuming we're outside the simple case of empty drives). The performance penalty, especially on large disks, is unacceptable, so we typically allow fragmentation now to speed the initial write. Subsequent reads and writes can greatly suffer, which is why FAT is always inappropriate if alternatives are available.

You don't have to scan the entire disk to find sufficient free space.  All you have to do is find a reasonable amount of free space, not the largest possible, and make sure that you don't start allocating blocks for the new file that immediately follow a block allocated to another file, especially when that file is still open and being written to.  And certainly do not allocate a single free block that sits between two allocated ones.  That goes a long way to minimizing fragmentation.

---

