---
title: "path for other half of partition"
date: 2010-02-15
forum: General Help
---

### Post by badperson on 2010-02-15
Hi,
I'm setting up an ubuntu server (command line only)and when I installed ubuntu, i instructed it to use a partition of half the drive. 

What is the path of the other half of the partition? 

I have these folders under "/":
> bin  boot  cdrom  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  sbin  selinux  srv  sys  tmp  usr  var  vmlinuz


---

### Post by blueridgedog on 2010-02-15
Based on your description, the other half of the drive is empty unpartitioned space.  To use that space, you would need to partition and format it using fdisk and mkfs.  Once created and formated, the partition can be mounted with mount or added to your /etc/fstab file for automatic mounting at system boot.  I can assist you with the commands if needed.

---

### Post by badperson on 2010-02-15
that would be great, thanks....I used [this documentation]("https://help.ubuntu.com/community/InstallingANewHardDrive") to install a 2nd drive, but forgot about the other partition on the main drive. 
bp

---

### Post by blueridgedog on 2010-02-16
Assuming it is your first hard drive it will be /dev/sda.  If it is not sda, change the following as needed.  

To make a new partition on /dev/sda from the command line, you will use fdisk, with:

```
sudo fdisk /dev/sda
```

The first thing I like to do in fdisk mode is to enter "p" to print the current table.  You can see a menu of commands via "m".  The options are:

```
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
```

So, to create a new partition using empty space, enter "n" for new partition, then "p" to make it a primary, then "2" to make it your second primary partition.  Specify the start and stop points (I assume you want to use the entire disk).

Once created enter "t" to toggle the partition type, you can enter "L" to list the codes.  Enter code 83 for a Linux partition type.

Once done, verify that you have the partition table you want with "p" to print the table as currently defined.  If you are happy, use "w" to write it to the disk.

If you used sda and the second partition, you just created a partition called /dev/sda2.   To format it you use:

```
sudo mkfs.ext3 /dev/sda2 
```

or 

```
sudo mkfs.ext4 /dev/sda2
```

Whichever you prefer (one uses ext3 and the other ext4 for the file system).

WARNING:  You will mess things up if you are not certain as to the drive (sda) and partition (sda2) you are working on.  Double check everything and always have a backup of your data.

Once formated you can mount it anywhere you want, for example

```
sudo mkdir /files
sudo mount /dev/sda2 /files
```

Or...put an appropriate line in /etc/fstab to automount it:

```
/dev/sda2 /files      ext3    defaults        0       2
```

---

### Post by badperson on 2010-02-19
thanks, 
before I continue, I want to make sure I'm doing the right thing. 
The drive is 1TB in size, and I have ubuntu installed on it. I want to use the second part of the drive as a code repository. (I'll probably install git)

Here's the result of sudo lshw -C disk

> sudo lshw -C disk
[sudo] password for jason:
  *-disk:0
       description: ATA Disk
       product: WDC WD10EADS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCAV51011310
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0006fa34

and sudo fdisk /dev/sda -l

> sudo fdisk /dev/sda -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006fa34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121570   976510993+  8e  Linux LVM
/dev/sda2          121571      121601      249007+   5  Extended
/dev/sda5          121571      121601      248976   83  Linux
jason@jason-server:~$




Is it already partitioned? do I just need to format sda2...which looks like it takes up the second part of the drive? 

thanks, 
bp

---

### Post by blueridgedog on 2010-02-20
What is the output of the command

```
mount
```

and
```

df
```

---

### Post by oldfred on 2010-02-20
You need to understand partitioning a little more. sda2 is just an extended partition holding your linux install in sda5.


It looks like the entire disk is LVM partitioning. Which I do not use.
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

