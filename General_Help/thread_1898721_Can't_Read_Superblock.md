---
title: "Can't Read Superblock"
date: 2011-12-22
forum: General Help
---

### Post by JediMasterOdd on 2011-12-22
Hi Lads and Lasses,

I've been toying with Ubuntu on and off for a while now but still know very little about what I'm doing, I can use Google to find resolutions to  most problems though.

My USB thumb drive can not be mounted as the Superblock can't be read. I would use Windows to reformat the drive however, I would like to keep the data on the drive if possible.

**Error Message:** Error mounting: mount: /dev/sdc: can't read superblock

I have been Googling for a while and came across the below some ideas that I then tried.
The commands and the results are below. Commands are in **bold**.
 
I gather that the first one only lists partitions(?) on the drive but I thought someone might find it more helpful than I do.
```
**sudo fdisk -l /dev/sdc**

Disk /dev/sdc: 8103 MB, 8103395328 bytes
250 heads, 62 sectors/track, 1021 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdc2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdc3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdc4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

``````
**dumpe2fs /dev/sdc1 | grep superblock**
dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs: No such file or directory while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

```This one (below) brings up another window (some kind of disk management?) but I can't select /dev/sdc (the USB thumb drive)
```
**sudo pysdm**
[sudo] password for <Insert Username Here> 

(pysdm.py:4897): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(pysdm.py:4897): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(pysdm.py:4897): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(pysdm.py:4897): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```I have also had a read of this article [here]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/") (Linux Expresso). However, I can't figure out how to transpose it to FAT32.

Any ideas?

---

### Post by TeoBigusGeekus on 2011-12-22
Try checking the partitions for errors and correcting them with fsck:
```
sudo fsck /dev/sdc1
sudo fsck /dev/sdc2
sudo fsck /dev/sdc3
sudo fsck /dev/sdc4
```

---

### Post by JediMasterOdd on 2011-12-22
Thanks for the suggestion, but it's apparently not available.

This is the same for /dev/sdc1, 2, 3 and 4
```
**sudo fsck /dev/sdc1**
[sudo] password for <insert Username Here>: 
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: No such file or directory while trying to open /dev/sdc1
Possibly non-existent device?

```However...
```

**sudo fsck /dev/sdc**
fsck from util-linux 2.19.1
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
/
  Contains a free cluster (2). Assuming EOF.
FAT32 root dir starts with a bad cluster!

```

---

### Post by killermist on 2011-12-22
Is the Filesystem something other than ext2/3/4?  Like xfs, jfs, reiser(4)?
If so, then doing checks for ext2/3/4 will obviously fail.

---

### Post by killermist on 2011-12-22
Try this:
```
sudo su
for count in 1 2 3 4; do mkdir /mnt/sdc$count; mount /dev/sdc$count /mnt/sdc$count; done
exit

```
paste the output (which should show any mount failures or whatnot), and also the output (after the command string) of
```
df -hT
```

---

### Post by JediMasterOdd on 2011-12-22
As requested:
```
**for count in 1 2 3 4; do mkdir /mnt/sdc$count; mount /dev/sdc$count /mnt/sdc$count; done**
mount: special device /dev/sdc1 does not exist
mount: special device /dev/sdc2 does not exist
mount: special device /dev/sdc3 does not exist
mount: special device /dev/sdc4 does not exist
```

```

**df -hT**
Filesystem Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext4     36G  2.9G   32G   9% /
udev      devtmpfs    2.0G   12K  2.0G   1% /dev
tmpfs        tmpfs    793M  964K  792M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    2.0G  200K  2.0G   1% /run/shm

```

---

### Post by killermist on 2011-12-22
Is the drive a USB (or other external connected) drive?  Because the output of the commands indicates that the drive is not where it was when you were originally issuing it commands.

---

### Post by JediMasterOdd on 2011-12-22
Yes, It's a USB memory stick. It's meant to be FAT32

---

### Post by killermist on 2011-12-23
With it (potentially) changing places quasi-randomly, I can't give you specific commands.
If you know what the root device is that it moved to (like sdd or sde instead of sdc), you can substitute that in the commands I gave you, and that will give some useful output, hopefully.  
Of course, some quasi-failed attempts could start to populate your /mnt directory with subdirectories you may never use.  Though as unused/unpopulated directories their mere existence shouldn't harm anything.

---

### Post by JediMasterOdd on 2012-01-09
Sorry I have not replied earlier. I have been on holidays.

I have rerun the following script, specifically targeting the USB device (now /dev/sdb)
```
**df -hT /dev/sdb**
Filesystem Type    Size  Used Avail Use% Mounted on
udev      devtmpfs    996M  4.0K  996M   1% /dev
```When I ran the below script, I had to break it up line by line as I have no idea how to make a  script, so I may have given a false reading
```
sudo su
for count in 1 2 3 4; do mkdir /mnt/sdc$count; mount /dev/sdc$count /mnt/sdc$count;
done exit
```Do you have a link with instructions for creating scripts?

Is it possible to copy a Superblock from another USB device to the corrupt one?

---

### Post by killermist on 2012-01-09
The operant line is:
```
for count in 1 2 3 4; do mkdir /mnt/sdb$count; mount /dev/sdb$count /mnt/sdb$count; done
```
"sudo su" just grabs superuser privileges (because you need them to create the directories and try the mounts)
and "exit" after executing the line just drops the superuser privileges, returning you to standard user again.

---

### Post by JediMasterOdd on 2012-01-10
Thanks :)

```
**for count in 1 2 3 4; do mkdir /mnt/sdb$count; mount /dev/sdb$count /mnt/sdb$count; done**
mount: special device /dev/sdb1 does not exist
mount: special device /dev/sdb2 does not exist
mount: special device /dev/sdb3 does not exist
mount: special device /dev/sdb4 does not exist

```

```
**df -hT /dev/sdb**
Filesystem Type    Size  Used Avail Use% Mounted on
udev      devtmpfs    996M  4.0K  996M   1% /dev

```

---

### Post by JediMasterOdd on 2012-01-11
Well, I have found the data I was trying to save, hidden away in a Hard Disk image I took a while ago.

Thanks for your efforts and ideas. I think I'll just reformat the USB drive

---

