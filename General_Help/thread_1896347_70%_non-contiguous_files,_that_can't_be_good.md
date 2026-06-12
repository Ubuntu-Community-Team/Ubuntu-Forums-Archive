---
title: "70% non-contiguous files, that can't be good?"
date: 2011-12-16
forum: General Help
---

### Post by Frozen Forest on 2011-12-16
I did get this data when I did run e2fsck, I guess that non-contiguous files indicate that a disk need to be defrag but how? Disk is a ext4.
```

e2fsck 1.41.14 (22-Dec-2010)
Lager1 has been mounted 114 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   10652 inodes used (0.04%)
    7454 non-contiguous files (70.0%)
       4 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 3699/6940/1
100577003 blocks used (91.32%)
       0 bad blocks
       2 large files

   10116 regular files
     523 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       4 symbolic links (2 fast symbolic links)
       0 sockets
--------
   10643 files


```

---

### Post by N00b-un-2 on 2011-12-16
ummm... EXT partitions don't need to defrag.  That's one of the huge advantages of Linux over Windows.  The way that the Linux file system works means that your files are only ever written to the next space that is large enough to accommodate them, in order to eliminate data fragmentation that is experienced on Windows architectures NTFS and FAT. The EXT file system may not be the most efficient use of physical space on a disk, but it is the most efficient in terms of data accession and writing.

But I digress.  Over long periods of time, after lots of data has been written, deleted and written again, small gaps can occur between file segments.  That's where Shake comes in.  Shake is a tool that recontiguates (is that a real word?) your file system, which will optimize read and write speeds and can free up additional space on a hard drive.

to install shake add the ppa

```
sudo add-apt-repository ppa:un-brice/ppa
sudo apt-get update
sudo apt-get install shake
```

to use shake, open a terminal and 
```
shake -v /my/directory
```
may take a while to complete.

---

### Post by matt_symes on 2011-12-16
Hi

Take a look at

```
man e4defrag
```

Image your hard drive first. 

I have never used the program so i can offer no advice. 

I have only read the man page.

Kind regards

---

### Post by N00b-un-2 on 2011-12-16
:( I just installed it to test, and apparently it no longer works on oneiric.  just spits out errors when run.

---

### Post by jerome1232 on 2011-12-16
The only time I've ever had fragmentation is

A. On a very, very full disk.
B. Torrenting (or streaming to a file in some other manner), adjusting my client to pre-allocate space fixed it.

Something is fishy if your disk is getting that fragmented in the first place imho.

Also it's been in the works for awhile now that an online ext4 defragger is beeing worked on and that it will automatically defrag things as the become fragmented, or so google tells me.

---

