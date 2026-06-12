---
title: "Hard drive #2 NOT found...."
date: 2012-01-23
forum: General Help
---

### Post by tonewheelkev on 2012-01-23
Disc Utility shows this drive to be present....but can't access files on it.

Is this PERMISSIONS....again!!???

---

### Post by Grenage on 2012-01-23
By cannot access the files, do you mean that you can see but not access them, or that you cannot even see them?  Is the drive mounted?

---

### Post by tonewheelkev on 2012-01-23
Mounted at: /media/500GB

500GB is name of drive......why it is mounted ion media...have no idea!!

---

### Post by Grenage on 2012-01-23
Media is the default for Ubuntu; I don't know why it's used.

Do you have read access to the files, or can you not enter /media/500GB?  You can either reset the permissions of the files/drive via terminal, or if the drive is going to be a permanent resident, add an entry to fstab (where you can set the mount point).

---

### Post by tonewheelkev on 2012-01-23
Whoooaaaaa Neddy!!!!

Although I've used Ubuntu for 2 years now....still a BEGINNER.....

So what do I do...? (Sorry....pathetic aren't I?)

---

### Post by tonewheelkev on 2012-01-23
PS....can't read the files either

---

### Post by Grenage on 2012-01-23
> **tonewheelkev said:**
> Whoooaaaaa Neddy!!!!

Although I've used Ubuntu for 2 years now....still a BEGINNER.....

So what do I do...? (Sorry....pathetic aren't I?)


I should have been more specific. :)

Before we start, do you know what filesystem the drive has?  If you can post the output of these commands, it will help:

```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

### Post by tonewheelkev on 2012-01-23
sudo fdisk -l
[sudo] password for kev: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b82ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    48828415    24413184   83  Linux
/dev/sda2        48830462   625141759   288155649    5  Extended
/dev/sda5        48830464    68360191     9764864   82  Linux swap / Solaris
/dev/sda6        68362240   625141759   278389760   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
kev@kev-H61M-D2-B3:~$ 

AND............

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=234529b4-c35e-468c-83f3-e90f03821e5e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=1801e14d-e845-42e7-95f8-7c10b1519aeb /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4fff4065-bcc6-48c3-8cbc-75caf82730b0 none            swap    sw              0       0
kev@kev-H61M-D2-B3:~$ 

AND finally..................

sudo blkid
/dev/sda1: UUID="234529b4-c35e-468c-83f3-e90f03821e5e" TYPE="ext4" 
/dev/sda5: UUID="4fff4065-bcc6-48c3-8cbc-75caf82730b0" TYPE="swap" 
/dev/sda6: UUID="1801e14d-e845-42e7-95f8-7c10b1519aeb" TYPE="ext4" 
/dev/sdb: LABEL="500GB" UUID="db2e6e68-6741-4593-916c-e222d6854d17" TYPE="ext4" 
/dev/sdd: LABEL="1.0 TB" UUID="ca83b9b9-ef18-4348-8cbf-ed4ca6a403cf" TYPE="ext4" 
kev@kev-H61M-D2-B3:~$ 

......WOW!!!!!

---

### Post by Grenage on 2012-01-23
> **tonewheelkev said:**
> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

**Disk /dev/sdb doesn't contain a valid partition table**


Would this be a new drive, per chance?  The reason you can't access any files is because it's not been partitioned/formatted, at least as far as the computer is concerned.

Assuming that's the case, you can unmount the drive, then run gparted to partition and format it.  From a console, you would type:

```
gksu gparted
```
If it is not installed, use:

```
sudo apt-get install gparted
```

You can unmount the drive in Nautilus. :)

---

### Post by tonewheelkev on 2012-01-23
Drive is formatted   EXT4   has 130GB of files on it....I hope!!

---

### Post by ajgreeny on 2012-01-23
Neither sdb nor sdd have valid partition tables, ie, no partitions on either disk.

Do you think they should both have partitions made already with some data on them, and if so, how were those partitions made?  It may simply be that the disks' partition tables have been corrupted in some way.

If the disks are empty, you can use gparted to make new partition tables on both of them using the gparted "Device" menu, and then make new partitions on each disk according to how you want to use them.

EDIT:
Too slow again!

Looks like a corrupt partition table if you think there should be 130GB data on sdb.

Maybe time for testdisk to try and reconstruct the partition table.  Or just make sure sdb is unmounted and run ```
sudo e2fsck /dev/sdb
```as that may sort out minor filesystem problems.

What about sdd?  Any problems with that?

---

### Post by oldfred on 2012-01-23
Did you format drive without creating partition(s)? I think such a thing is possible kinda like a floppy disk, but everything expects partitions.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Edit:
I thought it was Whoa Nelly!
[http://www.urbandictionary.com/define.php?term=whoa+nelly](http://www.urbandictionary.com/define.php?term=whoa+nelly)
But I learned it here as Grandpa sold horses when I was 3.
[http://answers.yahoo.com/question/index?qid=20070602060105AAy4FUY](http://answers.yahoo.com/question/index?qid=20070602060105AAy4FUY)

---

### Post by tonewheelkev on 2012-01-23
There are no partitions on the 500GB

ajgreeny's command returns:

sudo e2fsck /dev/sdb
[sudo] password for kev: 
e2fsck 1.41.14 (22-Dec-2010)
500GB: clean, 12440/30531584 files, 24495157/122096646 blocks

---

### Post by tonewheelkev on 2012-01-23
Of further note...
when I boot from CD (Try Ubuntu!!)...I can access the files on the 500GB drive....they are there!!!

---

### Post by efflandt on 2012-01-23
> **tonewheelkev said:**
> There are no partitions on the 500GB

ajgreeny's command returns:

sudo e2fsck /dev/sdb
[sudo] password for kev: 
e2fsck 1.41.14 (22-Dec-2010)
500GB: clean, 12440/30531584 files, 24495157/122096646 blocks

sdb is an entire drive.  So if you can e2fsck that, it makes it looks like you may have formatted the entire drive like a big floppy with no partitions on it.

If using gparted, you need to create an "msdos partition table" first, then the first primary or extended partition on sdb would be /dev/sdb1.  Do you have room somewhere to copy the files on that drive elsewhere before you do that (maybe after creating a partition table and 1 or more partitions on the other drive)?

---

### Post by ajgreeny on 2012-01-24
> **tonewheelkev said:**
> Of further note...
when I boot from CD (Try Ubuntu!!)...I can access the files on the 500GB drive....they are there!!!
In that case I would copy them to some other disk, perhaps your main disk sda, if there's room on partition sda6, then re-format the 500GB disk they came from, properly this time using gparted, and then boot back into your installed ubuntu and copy the files back to the 500GB disk/partition.

I admit to being baffled why the live CD can see the files when your installed version can not, but such are the wonders of technology, that I am never surprised when I am baffled.

---

### Post by tonewheelkev on 2012-01-24
Oh....and can now boot ONLY from the live CD

Trying to boot from 'successfully' installed version on hard drive, results in:

stopping system V runlevel compatibility....:confused:

---

