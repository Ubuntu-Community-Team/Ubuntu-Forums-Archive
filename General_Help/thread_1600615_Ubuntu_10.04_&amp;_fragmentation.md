---
title: "Ubuntu 10.04 &amp; fragmentation"
date: 2010-10-19
forum: General Help
---

### Post by quisnox on 2010-10-19
Situation:

I use computer for serious multimedia (audio) editing - often write/convert/delete/split lots of large files to my home partition. Currently all partitions are EXT4 and I've heard a lot of "hate talk" about this file system and fragmentation.

So, I wanna know the truth. 

1. Does Ext4 requires defragmentation?
2. If yes, how to do that, without full partition wipe-out?

---

### Post by TNT1 on 2010-10-19
**2.10. Online defragmentation**

  (This feature is being  developed and will be included in future releases). While delayed  allocation, extents and multiblock allocation help to reduce the  fragmentation, with usage filesystems can still fragment. For example:  You write three files in a directory and continually on the disk. Some  day you need to update the file of the middle, but the updated file has  grown a bit, so there's not enough room for it. You have no option but  fragment the excess of data to another place of the disk, which will  cause a seek, or allocate the updated file continually in another place,  far from the other two files, resulting in seeks if an application  needs to read all the files on a directory (say, a file manager doing  thumbnails on a directory full of images). Besides, the filesystem can  only care about certain types of fragmentation, it can't know, for  example, that it must keep all the boot-related files contiguous,  because it doesn't know which files are boot-related. To solve this  issue, Ext4 will support online fragmentation, and there's a e4defrag  tool which can defragment individual files or the whole filesystem.

From :
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

So go find e4defrag...

---

### Post by TNT1 on 2010-10-19
Ok, sorry, read here:
[http://ubuntuforums.org/showthread.php?t=1201298&page=2](http://ubuntuforums.org/showthread.php?t=1201298&page=2)

---

### Post by TBABill on 2010-10-19
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by TNT1 on 2010-10-19
> **TBABill said:**
> [https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)


This bit:
Another common Windows practice that is not needed in  Unix is defragmenting the hard drive.  When NTFS and FAT write files to  the hard drive, they don't always keep pieces (known as blocks) of  files together.  Therefore, to maintain the performance of the computer,  the hard drive needs to be "defragged" every once in a while.  This is  unnecessary on Unix File systems due to the way it was designed. When  ext3 was developed, it was coded so that it would keep blocks of files  together or at least near each other. 
**No  true defragmenting tools exist for the ext3 file system, but tools for  defragmenting will be included with the ext4 file system. **
?

---

### Post by TBABill on 2010-10-19
I think the point is that you can bring the blocks all back together (thinking for purposes like partitioning?) neatly, but unnecessary just to use as general housekeeping because similar blocks are automatically kept together in *nix based systems. This would keep the hard drive from searching for fragmented blocks to perform a single execution.

---

### Post by quisnox on 2010-10-19
Ok, I'm fool - ext4 is worse than ext3 or wtf?

At old times, people used Ext3 for years of heavy write/delete load and never used defragmenter.

I don't understand what's wrong with Ext4. And does I need to defragment.

[SIZE=2]
[SIZE=1]p.s. sorry for my poor English..[/SIZE][/SIZE]

---

### Post by TNT1 on 2010-10-19
go here: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
download pyfragtools, and post the output when you run it...

---

### Post by ean5533 on 2010-10-19
> **quisnox said:**
> I don't understand what's wrong with Ext4. And does I need to defragment.

Current implementations of ext4 support online de-fragmentation the same as ext3. This means that ext4 does just as good a job as ext3 did of keeping files from being fragmented*.

So no, you don't NEED to defragment. De-fragmenting tools exist for ext4 just as they did for ext3, but the gains will be minimal. In other words, don't waste your time.

*Actually, ext4 does an even BETTER job than ext3 of keeping large files defragmented, due to the use of "extents". Extents only work on partitions that were originally created as ext4, not for partitions that were converted from ext3.

---

### Post by psusi on 2010-10-19
> **TNT1 said:**
> This bit:
**No  true defragmenting tools exist for the ext3 file system, but tools for  defragmenting will be included with the ext4 file system. **
?

Actually that is not true.  See launchpad.net/e2defrag.

It was originally written in the 1990s but work was done to improve the block allocator in the kernel to the point that defragmenting became generally unnecessary in practice, because pedantic levels of fragmentation do not occur like under windows.  As a result, nobody bothered using the defragger, and it was abandoned.  I rescued the code from the bit bucket and updated it to work on ext3 and ext4 so I can use it in conjunction with ureadahead to speed up boot times.

> **ean5533 said:**
> 
*Actually, ext4 does an even BETTER job than ext3 of keeping large files defragmented, due to the use of "extents". Extents only work on partitions that were originally created as ext4, not for partitions that were converted from ext3.

Extents do have their benefits, but they don't really affect fragmentation one way or the other.  If you convert to ext4, they also work just fine; it's just that enabling extents does not convert existing files to use them.  You can do that with chattr +e.

---

### Post by ean5533 on 2010-10-19
> **psusi said:**
> Extents do have their benefits, but they don't really affect fragmentation one way or the other.  If you convert to ext4, they also work just fine; it's just that enabling extents does not convert existing files to use them.  You can do that with chattr +e.

I'm certainly no expert on the subject, but my understanding is that extents help prevent fragmentation of large files because it clusters large parts of the file together into the extent.

A quick google search for "ext4 extents fragmentation" seems to confirm. Here's a snip from the Wikipedia article on ext4 (emphasis mine):

> An extent is a range of contiguous physical blocks, improving large file performance and **reducing fragmentation**

---

### Post by psusi on 2010-10-19
Yea, that's not really true.  Without extents the blocks themselves are typically allocated in contiguous chunks, but every single block number must be explicitly listed in an indirect block.  With extents, only the first block number and the count of blocks in that extent must be listed ( roughly ).  The end result is that without extents, a few more blocks have to be allocated for indirect blocks to list the blocks that actually hold the data, but there isn't really any effect on the data blocks themselves.

I suppose it depends on your semantics.  If you consider a sequence of blocks like DDDIDDD where D is data and I is indirect block to be a fragmented file, then yes, extents can reduce fragmentation.  I don't really consider that to be the case since the head does not have to seek while reading the file since that I block has to be read before you can know you need to read the last 3 Ds anyhow.  Fsck seems to agree that such a file is not fragmented.

---

### Post by quisnox on 2010-10-19
I've checked [this long and boring article]("http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/") about Linux, defragmenting, ext4 developers, blah blah blah

and found a _**perfect solution**_ in the comments:

[IMG]http://img205.imageshack.us/img205/8079/screenshotpj.png[/IMG]

Now I can **_recommend_ **this to others, because it looks like best choice. 

No, seriously - it seems Ext4 is a joke - nobody cares about home-computing, but it's DEFAULT Ubuntu's FS.

---

### Post by c-shadow on 2010-10-21
> **quisnox said:**
> Situation:

I use computer for serious multimedia (audio) editing - often write/convert/delete/split lots of large files to my home partition. Currently all partitions are EXT4 and I've heard a lot of "hate talk" about this file system and fragmentation.



If I can make a suggestion: xfs.
A while ago with ext3 I bumped into a real problem with fragmentation. I had a 600 GB partition under ext3 which was about 80-90% full all the time (which is a really bad thing for ext3) with about 70% large files (couple of GB each). Also a lot of deleting/appending/moving files between the disks was going on. One day I measured a file transfer of about 9MB/s, from that ext3 partition to /dev/null - and that was on the disk that can easily do about 70+ MB/s! With time, that partition became so fragmented that working with large files was a real pain in the...
That was before ext4. I guess that now with ext4, delayed allocation and extents it would perform better than ext3, but never tried. I solved the problem by deleting the partition and formatting as xfs which is designed to work with large files. With a few mount tweaks it works fine also with smaller files. Most iritating under ext3 was deleting 20 GB files, it took ages. On XFS it is instantaneous. It is a mature filesystem, it has online defragmenter and all the features like ext4. Works like a charm since then :)

---

