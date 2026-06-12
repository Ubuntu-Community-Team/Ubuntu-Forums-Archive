---
title: "Non-Destructive CLI NTFS Resize"
date: 2012-05-07
forum: General Help
---

### Post by Jolladay on 2012-05-07
Hi all,

I am working on a project where I am using various tools in NTFSProgs and a python script in Ubuntu to capture windows 7 images and later apply those images to new drives.

I am at the point where I can create the partitions and apply the images with dd and NTFSClone. 

I now need to extend the last partition/file system to fill any remaining disk space.

In my searching and googling I have only found suggestions that use GParted. This will not work for me as I need to use a Python script to run CLI commands to complete this task.

Does anyone know how this can be done?

Thank you!

-Jolladay

---

### Post by Cheesemill on 2012-05-07
Funnily enough the back end program that gparted uses is called ntfsresize :)

```
man ntfsresize
```for details.


In it's simplest form (which is probably what you want) then
```
ntfsresize /dev/sda2
```would resize the NTFS partition sda2 to take up the remaining free space.

---

### Post by Jolladay on 2012-05-07
Hi, thanks for the reply!

I am indeed using ntfsresize to resize the NTFS file system. However, I also need to resize the actual partition. Just to be sure, I ran:

ntfsresize /dev/sda2

It told me "Nothing to do: NTFS volume size is already OK."

Meaning, the FS is already taking up the whole partition.

But, I have about 800 mb of empty space following /dev/sda2 that I would like to use. With other drives, it will be more like 16 gigs of empty space.

In my mind I think it should happen like so:

Expand /dev/sda2 partition
then
expand NTFS filesystem with NTFSResize.

I just don't know how to expand the partition from the CLI.

-Jolladay

---

### Post by Cheesemill on 2012-05-07
From 'man ntfsresize'
> [NOPARSE]   Enlargement
       To  enlarge  an  NTFS filesystem, first you must enlarge the size of the underlying partition. This can be done using fdisk(8) by deleting the partition and
       recreating it with a larger size.  Make sure it will not overlap with an other existing partition.  You may enlarge  upwards  (first  sector  unchanged)  or
       downwards  (last  sector  unchanged),  but  you  may  not  enlarge at both ends in a single step.  If you merge two NTFS partitions, only one of them can be
       expanded to the merged partition.  After you have enlarged the partition, you may use ntfsresize to enlarge the size of the filesystem.
[/NOPARSE]

If in doubt, **read the man page** !!!

---

### Post by Jolladay on 2012-05-07
:)

I have read the man for NTFSResize several times. This brings me to my issue, fdisk and GParted both appear to work great. However, I can't use either of these (as far as I'm aware) in a python script.

FDisk has an interactive system for creating partitions and GParted uses a GUI.

I need to be able to provide a single command that will resize the partition to fill the entire remaining disk.

---

### Post by Cheesemill on 2012-05-07
What you could do is use gparted from a Live CD to carry out the required operation, and then look at the gparted logs when it has completed to see exactly what commands it has used.

Give me a minute, I'll test in a VM and get back to you.

---

### Post by Cheesemill on 2012-05-07
OK then, unfortunately the gparted logs only show the exact ntfsresize  commands used, not the other ones we're after. However, after a bit of  digging it turns out you use parted to delete and create the partition.

The following shows resizing an NTFS partition from 5GB to 10GB if you can follow along.....

```
root@xubuntu:~# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
138 heads, 12 sectors/track, 25327 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000367de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    10242047     5120000    7  HPFS/NTFS/exFAT
root@xubuntu:~# 
root@xubuntu:~# 
root@xubuntu:~# 
root@xubuntu:~# parted /dev/sda rm 1   [COLOR=Red]# DELETE THE EXISTING PARTITION[/COLOR]
Information: You may need to update /etc/fstab.                           

root@xubuntu:~# parted /dev/sda mkpart primary NTFS 2048s 20000000s  [COLOR=Red]# RECREATE THE PARTITION WITH NEW END SECTOR[/COLOR]
Information: You may need to update /etc/fstab.                           

root@xubuntu:~# ntfsresize -f /dev/sda1  [COLOR=Red]# RESIZE THE FILESYSTEM[/COLOR]
ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 5242876416 bytes (5243 MB)
Current device size: 10238951936 bytes (10239 MB)
New volume size    : 10238947840 bytes (10239 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 27 MB (0.5%)
Collecting resizing constraints ...
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sda1'.
root@xubuntu:~# 
root@xubuntu:~# 
root@xubuntu:~# 
root@xubuntu:~# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000367de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20000000     9998976+   7  HPFS/NTFS/exFAT
root@xubuntu:~# 
```Please note this is only a quick proof of concept on a VM with an NTFS partition that contains no data.
You would obviously have to parse the output of commands such as fdisk or parted first to get the values of the start and end sectors of the partition.

---

### Post by Jolladay on 2012-05-07
Thanks for doing that, I will try that out and respond with the outcome.

-Jolladay

---

### Post by Jolladay on 2012-05-07
Fantastic!

I was able to use Parted to recreate the partition, filling up the remaining disk.

sudo parted /dev/sda --script print
sudo parted /dev/sda --script rm 2                   # Removes the second partition, /dev/sda2
sudo parted /dev/sda --script print
sudo parted /dev/sda --script -- mkpart primary NTFS 106MB -1 # Makes the partition fill the whole disk
sudo parted /dev/sda --script print
sudo ntfsresize /dev/sda2

The 106MB was the starting point of the partition, sda2.

Thanks very much for your help!

Now... to figure out how to parse the starting point of the partition printed from the parted "print" command.

-Jolladay

---

### Post by Cheesemill on 2012-05-07
Use the -m switch to create parsable output:
```
sudo parted /dev/sda --script -m print
```Then pipe it into cut to get the second column and then tail to get the last line:
```
parted /dev/sda --script -m print | cut -d : -f 2 | tail -n 1
```To give you the starting point of the last partition.


Final command:
```
sudo parted /dev/sda --script rm 2 && sudo parted /dev/sda --script mkpart primary NTFS `parted /dev/sda --script -m print | cut -d : -f 2 | tail -n 1` -1 && sudo ntfsresize /dev/sda2
```I'm a beginner in bash scripting really so I'm making this all up as I go along, I'm sure that there is a neater way of doing all of this :)

---

### Post by Jolladay on 2012-05-09
That's exactly what I needed! Thanks very much. I'm also learning quite a bit about shell scripting and these are useful techniques.

-Jolladay

---

