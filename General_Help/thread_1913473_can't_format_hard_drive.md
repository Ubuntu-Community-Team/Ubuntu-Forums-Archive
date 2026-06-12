---
title: "can't format hard drive"
date: 2012-01-22
forum: General Help
---

### Post by Rigodonize on 2012-01-22
Hello. Thanks for reading this...

I was formating my hard drive and the computer shut down during the process. Now it shows it has more Gb than it should, I cant format it again either in windows or ubuntu...

It says it has no label and unrecognized partition...

I'm a bit new to all this so please, if you have any idea try to explain it for dummies...

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-01-22
try making a new partition table
in gparted it is under the device menu 
make sure you are on the correct hdd when you click it i can't stress that enough

---

### Post by Rigodonize on 2012-01-23
> **pqwoerituytrueiwoq said:**
> try making a new partition table
in gparted it is under the device menu 
make sure you are on the correct hdd when you click it i can't stress that enough


Thanks I tryed that but no luck...

I am on live cd with only one HDD. 

This are the error messages:

A partition table is required before partitions can be added.
To create a new partition table choose the menu item:
Device --> Create Partition Table.

create a partition table:
Error while creating partition table.


unrecognized disk label input/output error while write on/dev/sda
/dev/sda:unrecognised disk abel


And the disk Utility:

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sda: Input/output error

Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sda: Input/output error

---

### Post by mister_playboy on 2012-01-23
input/output error may be a mechanical problem with the HDD.  Is the drive making any clicking noises?

---

### Post by Rigodonize on 2012-01-23
no, no noises... it was working ok but as I said he formating process got interrupted half way through and I think that's the problem... I hope...

---

### Post by Paddy Landau on 2012-01-23
Interrupted formatting should not prevent you from manipulating your partitions.

From your Live CD, please open a terminal (Ctrl-Alt-T). Enter the following command, and paste the results here:
```
sudo parted --list
```The information will help us give you more help.

---

### Post by Rigodonize on 2012-01-23
> **Paddy Landau said:**
> Interrupted formatting should not prevent you from manipulating your partitions.

From your Live CD, please open a terminal (Ctrl-Alt-T). Enter the following command, and paste the results here:
```
sudo parted --list
```The information will help us give you more help.


ubuntu@ubuntu:~$ sudo parted --list
Error: /dev/sda: unrecognised disk label

---

### Post by stefangr1 on 2012-01-23
> **Paddy Landau said:**
> Interrupted formatting should not prevent you from manipulating your partitions.

From your Live CD, please open a terminal (Ctrl-Alt-T). Enter the following command, and paste the results here:
```
sudo parted --list
```The information will help us give you more help.

I guess this command isn't working simply because the partition is broken.

I'd advice you to manually partition it using fdisk. [Have a look at this thread]("http://ubuntuforums.org/showthread.php?t=282018") for a start on how you can do that.

---

### Post by Rigodonize on 2012-01-23
when I star fdisk I get this message:

ubuntu@ubuntu:~$ sudo parted --list
Error: /dev/sda: unrecognised disk label                                  

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.
Error: /dev/fd0: unrecognised disk label                                  

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label                                  

ubuntu@ubuntu:~$ sudo fdisk /dev/sda
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x541b3278.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

---

### Post by Rigodonize on 2012-01-23
Oh, I'm so useless... I think though I made some progress...

I get this when I type sudo parted --list
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.


and this is also different:

ubuntu@ubuntu:~$ sudo fdisk /dev/sda
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xb5a16d98.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.



Am I in the right path?? Thanks to all of you for helping...

---

### Post by stefangr1 on 2012-01-23
> **Rigodonize said:**
> Am I in the right path?? Thanks to all of you for helping...

What happens if you run:

```
sudo fdisk /dev/sda 
```

Choose "n" to create new partition table. Then choose "p", choose the appropriate values, and finally choose "w" to write changes to the disk.

Please note that /dev/sda refers to the disk that is to be partitioned, and that all data on that disk will be lost when it is repartitioned. A minor mistake in the above commands can thus easily result in a lot of data loss...

---

### Post by Rigodonize on 2012-01-25
Well, I managed to format last night... Thanks to all who helped...

---

### Post by Paddy Landau on 2012-01-25
Excellent! Well done.

---

### Post by tcam on 2012-08-14
Hey Rigodonize, would you please tell us how did you manage it to work? I am having the very same problem here, and can't make it work.

---

### Post by drmrgd on 2012-08-14
> **stefangr1 said:**
> What happens if you run:

```
sudo fdisk /dev/sda 
```

Choose "n" to create new partition table. Then choose "p", choose the appropriate values, and finally choose "w" to write changes to the disk.

Please note that /dev/sda refers to the disk that is to be partitioned, and that all data on that disk will be lost when it is repartitioned. A minor mistake in the above commands can thus easily result in a lot of data loss...

Depending on what your issue is and what you've tried, this is the procedure here.  Be sure to change the path from /dev/sda/ to the hard drive you really want to format!  

If this is still giving you an error, please post that here so we can get a better idea of what's going on.

---

### Post by tcam on 2012-08-14
This is what shows up in the screen:

ubuntu@ubuntu:~$ sudo parted --list
Error: /dev/sda: unrecognised disk label                                  

Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2004MB  2004MB  fat32


ubuntu@ubuntu:~$ sudo fdisk /dev/sda
fdisk: unable to read /dev/sda: Input/output error

---

### Post by r0xtehem0x on 2013-05-18
> **tcam said:**
> Hey Rigodonize, would you please tell us how did you manage it to work? I am having the very same problem here, and can't make it work.

In case someone else comes along and needs help with this, I had the same issue (with a Western Digital My Passport) and resolved it.

Issue:
I got into the issue by partitioning the disk with "Disk Utility" on Ubuntu 12.04.  I chose to use "Master Boot Record" for the scheme.  When I formatted the partition, I used NTFS with disk encryption.  After entering a passphrase the partitioning failed.  I then couldn't reformat the disk or anything with Disk Utility.

Resolution:
I installed "gparted" and removed the partition that had the failure.  I was then able to use Disk Utility again to format the hdd with no scheme (don't partition) and NTFS without disk encryption.  I'm sure the other options would work as well, just not the combo I chose earlier.

---

