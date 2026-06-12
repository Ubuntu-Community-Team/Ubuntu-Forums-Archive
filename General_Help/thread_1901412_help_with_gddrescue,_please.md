---
title: "help with gddrescue, please"
date: 2011-12-28
forum: General Help
---

### Post by kurja on 2011-12-28
I`ve been reading manuals and instructions all over the web but for some (probably very simple?) reason can`t run ddrescue. I`ve booted with a live CD and my situation is this ```
ubuntu@ubuntu:/media/USB DISK$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d6515f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   42  SFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders
Units = cylinders of 2816 * 512 = 1441792 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2782     3915744+   c  W95 FAT32 (LBA)

```I`m trying to recover data from a failing sata disk to another, new, 1TB sata disk, but apparently can`t get the ddrescue command syntax right. I`ve tried a whole bunch of variations on the theme and received two kinds of errors, ```
ubuntu@ubuntu:/media/USB DISK$ ddrescue –n /dev/sda1 /dev/sdb
ddrescue: cannot open input file: No such file or directory

```Or, when trying to define that I want the logfile on a USB stick, ```
ubuntu@ubuntu:/media/USB DISK$ ddrescue –n "/dev/sda" "/dev/sdb" ddlogfile
ddrescue: too many files

```The latter probably has something to do with that there are spaces in the path to the usb stick? Will the logfile be located at the `prompt path`, if no other is specified? Why does it say that there is no such file or directory, tried dev/sda or dev/sda1?

I do have the most important data backed up, but not quite everything. Any help would be much appreciated.

---

### Post by westie457 on 2011-12-28
Hi to the best of my limited knowledge there is two available options to recover the files off the hard drive. The first option will be very limited because somehow the hard drive has been converted to a dynamic drive.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   42  SFS

Only Windows can understand this. You could try to convert the drive back to normal with no guarantee of success then use Testdisk and Photorec to recover the files.

The second option which will work is to connect the hard drive to a computer that is running Windows and recover them that way.

---

### Post by kurja on 2011-12-28
> **westie457 said:**
> Hi to the best of my limited knowledge there is two available options to recover the files off the hard drive. The first option will be very limited because somehow the hard drive has been converted to a dynamic drive.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   42  SFS

Only Windows can understand this. You could try to convert the drive back to normal with no guarantee of success then use Testdisk and Photorec to recover the files.

The second option which will work is to connect the hard drive to a computer that is running Windows and recover them that way.

Thanks for the response.

This disk had been on an XP computer before, but continued to work as before when I added a new drive on which I installed Ubuntu - the problem disk is used just for storage. My point being that it might have been a dynamic volume (?) before, but worked OK with Ubuntu. I didn`t use mirroring or such things with XP when the disk was used with it. It was just a single chunk of storage space, not a boot drive.

I`m also able to mount the disk in Ubuntu.

My understanding of ddrescue was that it would not care what volumes or partitions or file system a disk has, and it would just copy everything as-is - is this not correct?

---

### Post by LMHmedchem on 2011-12-28
As far as I know, dd_rescue just does a block by block copy from device to device if you are using it in that mode. It deosn't have any notion of file systems and such, so I don't see why it would matter if the disk was dynamic or not.

I think you may just have the path wrong. The drives may be mounted in media or something like that. I just did this, and I don't remember if I used dev/ or media/. I had to install ddrescue with sudo apt-get install ddrescue, so I don't know if I was using the same version.

I think I did something like,
ddrescue -v -l /home/ubuntu/desktop/logfile dev/sda  dev/sdb

you might try without the -n.

LMHmedchem

---

### Post by kurja on 2011-12-28
> **LMHmedchem said:**
> As far as I know, dd_rescue just does a block by block copy from device to device if you are using it in that mode. It deosn't have any notion of file systems and such, so I don't see why it would matter if the disk was dynamic or not.

I think you may just have the path wrong. The drives may be mounted in media or something like that. I just did this, and I don't remember if I used dev/ or media/. I had to install ddrescue with sudo apt-get install ddrescue, so I don't know if I was using the same version.

I think I did something like,
ddrescue -v -l /home/ubuntu/desktop/logfile dev/sda  dev/sdb

you might try without the -n.

LMHmedchem

wait, you`re using ```
ddrescue (parameter) (logfile) (infile) (outfile)
```? does that work?

sigh, I guess I`ll just try to copy everything and see what I can get...

---

### Post by kurja on 2011-12-28
> **LMHmedchem said:**
> 

I think you may just have the path wrong. The drives may be mounted in media or something like that. I just did this, and I don't remember if I used dev/ or media/. I had to install ddrescue with sudo apt-get install ddrescue, so I don't know if I was using the same version.


LMHmedchem

It`s GNU ddrescue version 1.11

And I made sure both disks were unmounted.

---

### Post by LMHmedchem on 2011-12-28
I think I was using a different version of dd_rescue. Try running,

sudo apt-get install ddrescue

If it installs, try the syntax I posted with ddrescue and not gdd. You could also see if you can use media in the path and not dev. I think the version I use has a different syntax. You have to use -l to get a logfile and the logfile name goes after the flag.

ddrescue -v -l /home/ubuntu/desktop/logfile dev/source  dev/destination

If that doesn't work, you may just have to use cp. If you do,

cp -Rfp sourceDir/ destDir/ >& /home/ubuntu/desktop/copylog

the copy log file will have a list of things that couldn't be opened.

LMHmedchem

---

### Post by kurja on 2011-12-28
> **LMHmedchem said:**
> I think I was using a different version of dd_rescue. Try running,

sudo apt-get install ddrescue

If it installs, try the syntax I posted with ddrescue and not gdd. You could also see if you can use media in the path and not dev. I think the version I use has a different syntax. You have to use -l to get a logfile and the logfile name goes after the flag.

ddrescue -v -l /home/ubuntu/desktop/logfile dev/source  dev/destination

If that doesn't work, you may just have to use cp. If you do,

cp -Rfp sourceDir/ destDir/ >& /home/ubuntu/desktop/copylog

the copy log file will have a list of things that couldn't be opened.

LMHmedchem

Thanks for all the help,

I tried simply copying all the important files from the iffy disk and it appears to have succeeded. Just in case, I'll be bookmarking this thread however...

---

### Post by kurja on 2011-12-28
> **kurja said:**
> Thanks for all the help,

I tried simply copying all the important files from the iffy disk and it appears to have succeeded. Just in case, I'll be bookmarking this thread however...


update: while running off the live cd, everything seemed fine, now that I've restarted from the hard disk apparently I no longer "have the permissions necessary to view the contents of " that disk. Hm. The disk seems to be fine, I just can't read anything from it...

---

### Post by kurja on 2011-12-28
If I ```
sudo nautilus
``` then I can view the files. Permission problem of some sort, but how to fix?

---

### Post by kurja on 2011-12-28
ran ```
sudo chown -R <username>:<username> <drive name>
```

now it's accessible!

---

