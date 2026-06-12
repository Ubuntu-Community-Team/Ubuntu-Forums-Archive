---
title: "Need help creating paritions from cli using parted"
date: 2009-10-01
forum: General Help
---

### Post by jbrown96 on 2009-10-01
I'm running ubuntu 9.04 without a GUI, and I just got a new 1TB drive with no partitions and no partition table. I can't seem to figure out how to use parted. I've basically copied several examples, but there's something wrong with them. 

Here's the sort of thing that I've been trying. ```
sudo parted /dev/sdb primary 0 1000.2
``` It all seems right, although I'm guessing about the 1000.2 part. What's wrong with this command? I know the drive works; I was usuing just before with dm-crypt (using the entire device as encrypted, hence the lack of partitions). I am also a little confused how I'm supposed to come up the start and end numbers (well not "start" really...); fdisk reports that the drive is 1000.2GB, but I have another identical disk and as ext4 it's ~917GB. Which number should I use, or is there a better way to find this?


Thanks for help.

---

### Post by Giblet5 on 2009-10-01
From the man page ```
man parted
```

KNOWN ISSUES
ext3  filesystem functionality does not currently work.

And, "primary" is not a listed parted command.

Why not use fdisk? It works. Well.

```
sudo fdisk /dev/sdb
```
Hit 'p' to print the partition table.
There's probably a FAT32 filesystem on it, so delete that.
Now, hit 'n' and Enter, to create a new partition. Make it a primary partition. Use the 't' command to set its type to "83" (ext3). Hit 'w' to write the table out and exit.

Now, you have to format it: ```
sudo mke2fs /dev/sdb1
```. Now you can mount it and use it.

---

### Post by jbrown96 on 2009-10-01
Thanks Gilblet5

Fdisk worked fine. Here's what I did if anyone else needs to do this:

1) sudo fdisk /dev/sdb (substitute with your device)
2) p will print out the partition table. For me, there wasn't anything because I didn't have a partition table
3) o to create a partition table
4) n to create an new partition. It will prompt you for the number of the partition -- choose 1 --, the start point -- choose the default (just press enter) --, and for the end, just press enter if you want to use the entire device; otherwise, you can enter a size (i.e. 50MB, 20GB; include the MB or GB). 
5) w to write the changes to disk.
6) ```
sudo mkfs.ext4 /dev/sdb1
``` to create a file system there. Ext4 is a good, fast filesystem.

---

