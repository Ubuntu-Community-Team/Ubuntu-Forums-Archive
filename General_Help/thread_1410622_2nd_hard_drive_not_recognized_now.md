---
title: "2nd hard drive not recognized now"
date: 2010-02-18
forum: General Help
---

### Post by williammanda on 2010-02-18
I have a 2nd hard drive (500 GB) that I keep my media on. When I tried to access it, it wasn't showing up in places or even places > computer. I used system > administration > disk utility. On the left hand side it shows the drive listed with the type and model number. Right under that it shows 500 GB Hard Drive unrecognized unknown or unused. If possible I would like to recover the media on this drive. I had setup this drive as ext3 and had it mount /media/sdb1. I can go to /media/sdb1 in the file browser but nothing is there. Any ideas?

---

### Post by williammanda on 2010-02-19
The smart status = disk is healthy.

---

### Post by ktat on 2010-02-19
do you know if you formatted the drive when you set it up as ext3?

---

### Post by williammanda on 2010-02-19
Yes I used gparted.

---

### Post by williammanda on 2010-02-19
Right now gparted says the file system is unknown. Also it says that it is unable to detect file system, possible reasons are: the file system is damaged, the file system is unknown to gparted, there is no file system available (unformatted). I'm wondering if the area that keeps the disk info has gotten corrupted?

---

### Post by lidex on 2010-02-19
What is the output of:
```
sudo fdisk -l
```

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1039092]("http://ubuntuforums.org/showthread.php?t=1039092")

---

### Post by amsterdamharu on 2010-02-19
what does the command
```
sudo fdisk -l
```
say?

---

### Post by williammanda on 2010-02-19
william@C2Q:~$ sudo fdisk -l
[sudo] password for william: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c7dd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648      121601   947465505    5  Extended
/dev/sda5            3648        4620     7815591   82  Linux swap / Solaris
/dev/sda6            4621      121601   939649851   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d417b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
william@C2Q:~$

---

### Post by williammanda on 2010-02-19
lidex
I installed and ran the testdisk program. I started testdisk by choosing "create log", selected HD sdb1, "proceed", "Intel", "Analyze", "quick search", Vista partitions - entered N, hit enter to continue. This the result of the 1st test. See attachment.

---

### Post by williammanda on 2010-02-19
I continued on with the next testdisk test by selecting enter and then deeper search. Looks as though everything went ok. See attached photo.

---

### Post by amsterdamharu on 2010-02-19
Lets see if it mounts, can you run the following commands and post the output?

```
sudo unmount /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
#if the prefious mount fails try:
sudo mount -t ext3 /dev/sdb1 /media/sdb1

```

Can you post what is in your /etc/fstab ?

---

### Post by williammanda on 2010-02-19
william@C2Q:~$ sudo unmount /media/sdb1
[sudo] password for william: 
sudo: unmount: command not found
william@C2Q:~$ sudo mount /dev/sdb1 /media/sdb1
mount: you must specify the filesystem type
william@C2Q:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by williammanda on 2010-02-19
I wanted to post some of the finding from an earlier post using Palimpsest Disk Utility. See attached photos.

---

### Post by amsterdamharu on 2010-02-19
Are you sure it is ext3? I cannot realy read the attached photos but have bad experience with Palimpsest Disk Utility (think it's a piece of cr@p but might be good in the future).

Just try to mount it as ext2 and ext4
```

sudo mount -t ext2 /dev/sdb1 /media/sdb1
sudo mount -t ext4 /dev/sdb1 /media/sdb1
```

How long have you used this partition? I usually have a backup of the mbr and partition table but since testdisk says there is nothing wrong I think it hasn't been formatted yet or partition table is damaged in which case testdisk should detect it and try to repair it.

---

### Post by williammanda on 2010-02-19
Yes it is ext3 I used gparted to format it and partition the drive when I first got it about a couple of years ago. The Palimpsest Disk Utility told me that the drive was ok (smart data). It just started this problem about 12 hours ago. I will try the other mounts as you suggest.

---

### Post by williammanda on 2010-02-19
william@C2Q:~$ sudo mount -t ext2 /dev/sdb1 /media/sdb1
[sudo] password for william: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

william@C2Q:~$ sudo mount -t ext4 /dev/sdb1 /media/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by amsterdamharu on 2010-02-19
[http://ubuntuforums.org/showthread.php?t=1410622&page=2](http://ubuntuforums.org/showthread.php?t=1410622&page=2)

Try testdisk dvanced menu, select the partition and choose Superblock, copy and paste the output here (no screenshot just select the text and right click it).

Before restoring anyting with testdisk make a backup:
```

sudo su
dd if=/dev/sdb of=/sdb.bin bs=512 count=1
dd if=/dev/sdb1 of=/sdb1.bin bs=512 count=1
```

---

### Post by williammanda on 2010-02-19
OK this is what I did after reading the testdisk website.

[http://www.cgsecurity.org]("http://www.cgsecurity.org")

1. I started here and followed along: (which some of theses steps are already stated in my previous posts)

[http://www.cgsecurity.org/wiki/Running_TestDisk]("http://www.cgsecurity.org/wiki/Running_TestDisk")

2. Then when get to Advanced menu select Superblock. The instructions for using are here.

[ext2/ext3: Find Backup SuperBlock]("http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock")

Once you find the 1st superblock then take that info and insert into this statement (change the bold text to yours) and run in terminal.

sudo /sbin/fsck.ext3 -b **24577** -B **1024** /dev/**hda1**

3. While this program is running it will ask you to approve every correction. I must have had over 1000 or so. It may take a hour or so to get through. Once you are finished reboot (optional).

4. After the reboot go in as root and view the changes. It recovered all my data but put it into several different folders named by numbers. I had to re-organize the folders to get them back to the way I wanted.

Now everything seems ok.

---

### Post by williammanda on 2010-02-19
> **amsterdamharu said:**
> [http://ubuntuforums.org/showthread.php?t=1410622&page=2](http://ubuntuforums.org/showthread.php?t=1410622&page=2)

Try testdisk dvanced menu, select the partition and choose Superblock, copy and paste the output here (no screenshot just select the text and right click it).

Before restoring anyting with testdisk make a backup:
```

sudo su
dd if=/dev/sdb of=/sdb.bin bs=512 count=1
dd if=/dev/sdb1 of=/sdb1.bin bs=512 count=1
```

I was doing part of what you ask while you posted. Thanks for your help!

---

### Post by amsterdamharu on 2010-02-19
Good to hear it worked, if you can find the time could you use the "thread tools" link to set this to solved?

The more I read about testdisk the more I believe it is a program sent from heaven. You should be considering getting a new harddisk or make sure all the realy important stuff is somewhere else too.

---

### Post by lidex on 2010-02-19
> **williammanda said:**
> william@C2Q:~$ sudo unmount /media/sdb1
[sudo] password for william: 
[COLOR="Red"]sudo: unmount: command not found[/COLOR]
william@C2Q:~$ sudo mount /dev/sdb1 /media/sdb1
mount: you must specify the filesystem type
william@C2Q:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

FYI/FFR, the unmount command syntax is "umount" _not_ "unmount"

---

### Post by ktat on 2010-02-22
I believe that when you format a drive you, effectively erase all the data on it.  If there are ways to recover this data - I don't know them, sorry.

---

