---
title: "29% fragmentation!?"
date: 2009-12-31
forum: General Help
---

### Post by nstgc379 on 2009-12-31
As some may have seen I've been considering formating my drives with ext4. Well I did. Before I did that I moved everything off onto another drive (it as actual quite the dance since the data was bouncing between 4 drives). So I've been copying data from one place to another, pretty much the only way of defragging a FS in Linux.

If this is too much information, please let me know. I've been critised for not including enough information before and I figured its better to provide too much then to leave something out.

Note that during these "tests" no hard drive activity, whether on the mentioned partitions or not, took place unless I say other wise. The two partitions used are on different drives and there should have been absolutely no activity on the drive other then what I will be mentioning.

The drive is 640GB (586.7GB) and has 199.1GB of free space. THat's 34% free space. Its used for data storage. This partition, along with every other parition I've made, was created using gparted.

```
   24742 inodes used (0.06%)
    7156 non-contiguous files (28.9%)
       9 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 23353/1372
96236183 blocks used (61.59%)
       0 bad blocks
       5 large files

   23557 regular files
    1169 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       7 symbolic links (7 fast symbolic links)
       0 sockets
--------
   24733 files

```

Something doesn't seem right. By switching to ext4 my fragmentation should have decreased. By repeatedly copying files, my fragmentation should have decreased.

Is there something I'm doing wrong. I have enough free space. On that drive.

So I decided to a newly created, empty ext3 partition. Its used for more temporary storage, a sort of waiting area (to be sorted). I put three files on that drive prior to this, I deleted them, and deleted the .trash folder. The drive is about 84GB (77.4GB) and is using 4.1GB of that for something. Its not showing up in the file manager. Thats not the point however (its probably overhead anyway), the point is it has 95% free space. I took a 16.1GB folder, copied it to this partition, then 5.3GB directory, and another 6.2GB. Two of those folders had videos of varying sizes and another parity files. The file count, given in the same order are {57,29,11}. I fsck'ed (sudo fsck -fv) the that partition and got the fallowing.

```
     111 inodes used (0.00%)
       6 non-contiguous files (5.4%)
       1 non-contiguous directory (0.9%)
         # of inodes with ind/dind/tind blocks: 86/85/0
 7625921 blocks used (36.98%)
       0 bad blocks
       1 large file

      94 regular files
       8 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     102 files

```

As expected, the fragmentation went down, however, my understanding is that fragmentation isn't suppose to exceed more then a few percent. Given that these are freshly created files on a new partition with plenty of space, I would expect lower numbers.

By then deleting these files from the larger (~640GB) partition, after fsck'ing I found these results (I then cleared out those directories from the trash can (I left the rest)).

Ooh, I accidentally said what I would do without actually doing it. I forgot to delete the files. Interestingly the file count increased by 3, but I'm not sure how.

After deleting the files and allowing the ext4 FS to work its delayed magic...

```
24644 inodes used (0.06%)
    7148 non-contiguous files (29.0%)
       9 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 23336/1291
88988355 blocks used (56.95%)
       0 bad blocks
       5 large files

   23465 regular files
    1163 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       7 symbolic links (7 fast symbolic links)
       0 sockets
--------
   24635 files

```

The file count went down by 98, the number of fragmented files was reduced by reduced by 8. The number of fragmented directories remained the same. The overall percentage went up, indicating that the files I selected weren't badly fragmented. In fact only 8 of the sected files were fragmented.

Now, after copying those back. At this time I have not checked their md5 files to make sure that they transfered properly, but I doubt there would be any trouble. Its also not particularly relevant.

```
   24744 inodes used (0.06%)
    7156 non-contiguous files (28.9%)
       9 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 23356/1371
96236185 blocks used (61.59%)
       0 bad blocks
       5 large files

   23559 regular files
    1169 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       7 symbolic links (7 fast symbolic links)
       0 sockets
--------
   24735 files

```


How wonderful, there are just as many fragmented files. I would have expected at least one file to come out clean. Well, this says nothing about the number of fragments.

At this point I made another md5 hash file on that drive, which increased the file count by one.

Using defragfs on a directory with various types and sizes of files. The total size of this directory's contents (on the 640GB parition) are approximately 24.1GB and 49 files. The file's range from a few kB to a few GB.

```
Total Files:			48
Fragmented Files:		42
File Fragmentation Rate:	87.5%
Avg File Fragments(1 is best):	18.5

```

I'd like to point out that the total file count given by defragfs is one less then it should be.

When I checked what had been transfered to the 84GB partition defragfs gave me the fallowing results.

```
Total Files:			48
Fragmented Files:		43
File Fragmentation Rate:	89.5833333333333%
Avg File Fragments(1 is best):	135.791666666667

```

and fsck returned

```
      66 inodes used (0.00%)
       6 non-contiguous files (9.1%)
       1 non-contiguous directory (1.5%)
         # of inodes with ind/dind/tind blocks: 43/42/0
 6704371 blocks used (32.51%)
       0 bad blocks
       2 large files

      48 regular files
       9 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
      57 files

```

Its fairly typical that they don't match. I'm not sure what criterion defragfs uses, nor do I know the method by which defragfs judges fragmentation, but I do trust fsck more.

fscking the 640GB partition after deleting the directory...

```
   24694 inodes used (0.06%)
    7151 non-contiguous files (29.0%)
       9 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 23346/1331
89908997 blocks used (57.54%)
       0 bad blocks
       4 large files

   23512 regular files
    1166 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       7 symbolic links (7 fast symbolic links)
       0 sockets
--------
   24685 files

```

The number of fragmented files decreased by 5. It definately seems as if defragfs cannot properly read the number of fragments on an ext4 partition. Oh well, it still can return the number of extents used. The total number of files decreased by 50, one more then expected.

I ran defragfs to see how many extents were used.

```
Total Files:			48
Fragmented Files:		42
File Fragmentation Rate:	87.5%
Avg File Fragments(1 is best):	42.9791666666667

```

The number more then doubled.

And now the last thing I will give is the fsck reults.

```
   24745 inodes used (0.06%)
    7156 non-contiguous files (28.9%)
       9 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 23359/1369
96236184 blocks used (61.59%)
       0 bad blocks
       5 large files

   23560 regular files
    1169 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       7 symbolic links (7 fast symbolic links)
       0 sockets
--------
   24736 files

```

The only thing thats noteworthy here is that the number of files, increased again.

So, whats going on here? From what I can tell from this, it appears as though any file I add will likely become fragmented just from being copied to the drive. On the 640GB, files are just stored there. They are created whole, not in sections with the exception of checksum tables and parity files.

---

### Post by pastalavista on 2009-12-31
Who knows? Is there a problem? Is something not working? Computers work in complex and mysterious ways. They make files just to remember where and when it made them. It's all just ones and zeroes anyway. Don't worry. Be happy.

---

### Post by dcstar on 2009-12-31
> **nstgc379 said:**
> As some may have seen I've been considering formating my drives with **ext4**. Well I did.
..........
Its fairly typical that they don't match. I'm not sure what criterion defragfs uses, nor do I know the method by which **defragfs** judges fragmentation, but I do trust fsck more.
.......

Why are you wasting your time with a tool that knows nothing about EXT4 (if their home page is anything to go by)?

---

### Post by nstgc379 on 2009-12-31
Is that the only tool I used? Did I not already acknowledge that defragfs isn't a good way of judging fragmentation? I know that the only release was 0.8 which came out in 2007. Ext4 hadn't been finished yet (its still in development I think). However, I was also using it on ext3 which it would work with. It also seems to be able to find the number of extents used. The number of extents used should not increase. More then either of those, I wished to include as much information as practically possible. If I was able to think up something else at that time I would have run that test as well.

---

