---
title: "limitation of folder capacity"
date: 2010-03-26
forum: General Help
---

### Post by kwanu on 2010-03-26
Hi all,
 
I am using the Ubuntu 9.04 and I have a trouble with the saving capacity for a single folder.
 
I mean...
I will save lots of files about 20000*7 files and it will be about 100GB.
But, my folder has a limitation to save the files, so I can not save 12.2GB more.
 
I was checked using the "du -sm". It said I have a limitation 12749MB for a single folder.
 
Do you guys know how can I save much more files, 12.2GB more.
 
Thanks,

---

### Post by rnerwein on 2010-03-26
hi
it depends on the kind of the file system you use ( ext2, ext3 ...). the other limit  is given on the inodes
wich you have for this file system. ( df -i ).
but on the other side if you got millions of files in one directory you will have much fun to search in this directory. best is: start a ls - go to the kitchen - cook your meal - eat - drink a coffee - go back and have a look if the ls finished !  :-)
ciao

---

### Post by kwanu on 2010-03-26
I think i am using the ext3, because I am using the Ubuntu in Window system.
So, do you guys know how can extend the capacity to save the files?
 
Thanks,

---

### Post by srs5694 on 2010-03-26
I've never before heard of a limit on the number of files in any given directory. This is distinct from a limit of the number of inodes (and therefore the number of files, since each file consumes one inode) in a single filesystem. Thus, if there's really a limit on the number of files in a single directory, I can't be of much help; however, if it's inode limitations you're running into....

Unfortunately, in ext2fs and ext3fs (and presumably ext4fs, although I've never checked this detail for it), the number of inodes is fixed when the filesystem is created. Thus, if you've run out of inodes on your partition, the only fixes will require you to back up at least some files -- you could create a new filesystem just for the directory/ies that hold the huge number of files and move just those files there, or you could back up everything, create a new filesystem on that partition, and restore it.

You may want to type "man mke2fs" and examine its -N option, which enables you to adjust the number of inodes the filesystem you create supports.

You may also want to look into alternatives to ext2/ext3/ext4. ReiserFS, in particular, doesn't pre-allocate its inodes, so you'll never run out of inodes if you use ReiserFS. ReiserFS also does a better job than other Linux filesystems at filling the available disk space with many small files, so you can fit more files on ReiserFS than you can on most other filesystems. Both features are unimportant for disks filled with large or average-sized files, but if you've got hundreds of thousands of small files (with sizes measured in the kilobytes), ReiserFS has an edge.

---

### Post by kwanu on 2010-03-27
Thanks for your comment.
 
That is my problem. I did not exactly know what is my problem.
So, I will try to fix this with your comment.
 
Thanks again.

---

### Post by asmoore82 on 2010-03-27
With ext3, there is a hard and fast limit of 32000 subdirectories per folder.
But files should indeed be limited only by the i-node count.

---

### Post by srs5694 on 2010-03-27
> **asmoore82 said:**
> With ext3, there is a hard and fast limit of 32000 subdirectories per folder.
But files should indeed be limited only by the i-node count.

Is that 32,000 *subdirectories* per directory or 32,000 *files* per directory? (Directories/subdirectories are of course just special files.) Do you know if there's a similar limit in other Linux filesystems (ext4, ReiserFS, XFS, JFS), and if so what it is?

---

### Post by RedRat on 2010-03-27
Good to know this. I know in the older Windows file system (FAT32), the root could only hold 512 files and/or directories, I think that changed with NTFS. Does Linux have some kind of limit for root???

---

### Post by asmoore82 on 2010-03-27
> **srs5694 said:**
> Is that 32,000 *subdirectories* per directory or 32,000 *files* per directory? (Directories/subdirectories are of course just special files.) Do you know if there's a similar limit in other Linux filesystems (ext4, ReiserFS, XFS, JFS), and if so what it is?

It's only *subdirectories*. The underlying cause is that any file can only have
32000 links to it, and each subdirectory will automatically have a link ("..") pointing
back to its parent. This is why the limit affects subdirectories and not files.

ext4 has increased the limit to 64000, with a workaround feature "dir_nlink" that
circumvents the limit altogether. However, the official "link count" on the actual i-node will
still not show higher than 64000.

I'm not sure about the other filesystems, but I'm getting all of these
gory details from wikipedia :razz:

---

### Post by srs5694 on 2010-03-28
I got curious and so I ran some tests, using a simple script to create 100,000 subdirectories in a directory on a USB flash drive on which I created various filesystems. Ext2fs has a limit of 31,998 subdirectories. ReiserFS and XFS both allowed over 100,000 subdirectories (I stopped creating them at this point). My JFS test is still ongoing, but it's up to 79,974. I haven't tried ext3fs or ext4fs, although I expect the ext3fs results would be identical to the ext2fs results. Ext2fs was *very* slow to unmount the media. I ended up pulling the USB flash drive I used rather than wait for the unmount. I didn't time these operations, but my impression is that ReiserFS and XFS were both faster than either ext2fs or JFS at creating the subdirectories.

---

