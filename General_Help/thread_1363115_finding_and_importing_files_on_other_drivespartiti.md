---
title: "finding and importing files on other drives/partitions"
date: 2009-12-24
forum: General Help
---

### Post by lekifsirk on 2009-12-24
Let me start by saying that I would not have started a new post if I had any idea what exactly I was searching for.  Sad but true.  Here is the situation...
I have a computer with Ubuntu 9.10 on it and it is fabulous.  I have a hard drive in this computer  with several partitions and installations of ubuntu as well as a partition with windoze xp.  I also have a second hard drive in there with who knows what os installed.  Now, my problem.  I don't know how to find and transfer files, photos, music, etc  to my newest partition/installation of U9.10.  I'd like to harvest all the files I need and then just format the extra space and merge it into my current system.
Any help would be greatly appreciated.
Happy Holidays everyone!

---

### Post by mikewhatever on 2009-12-24
Don't quite understand the problem, can you not copy/paste files from one drive to another, or do you have a hard time finding the files? Please explain yourself.

---

### Post by lekifsirk on 2009-12-24
It could be that I'm not sure even where to look for the files.  I apologize for my lack of knowledge.  It could be very simple, but I don't know where to look.  Although, when I look in the 'Places' menu I only see the current partition that has U9.10.  Is there somewhere else I should be looking?
Thanks for your reply.

---

### Post by oldfred on 2009-12-24
If you look in places, computer the left pane should show you all the other partitions that Ubuntu sees and it should see just about everything. It will not mount NTFS partitions that were not shut down normally or require a checkdisk in windows on reboot.

After you copy data over some info on planning partitions:
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partiti](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partiti)

---

### Post by Mahngiel on 2009-12-24
> **lekifsirk said:**
> Let me start by saying that I would not have started a new post if I had any idea what exactly I was searching for.  Sad but true.  Here is the situation...
I have a computer with Ubuntu 9.10 on it and it is fabulous.  I have a hard drive in this computer  with several partitions and installations of ubuntu as well as a partition with windoze xp.  I also have a second hard drive in there with who knows what os installed.  Now, my problem.  I don't know how to find and transfer files, photos, music, etc  to my newest partition/installation of U9.10.  I'd like to harvest all the files I need and then just format the extra space and merge it into my current system.
Any help would be greatly appreciated.
Happy Holidays everyone!

You're best bet is to create a partition (if you have the available space) in Fat32 format. this allows all OS's to read the partition.  Then you can individually move all your stuff from other OS's there and have universal access. 

This will allow you to use less space for each of your OS's, and concentrate all your media files in one place.

---

### Post by mikewhatever on 2009-12-24
> **lekifsirk said:**
> It could be that I'm not sure even where to look for the files.  I apologize for my lack of knowledge.  It could be very simple, but I don't know where to look.  Although, when I look in the 'Places' menu I only see the current partition that has U9.10.  Is there somewhere else I should be looking?
Thanks for your reply.

Hey, the lack of knowledge isn't a crime, on the contrary, it's a perfectly normal state. Anyway, thanks for explaining.
Theoretically, the links to all other partitions should have been in the Places menu. Let's verify what partitions you have as seen by Ubuntu. Can you open Applications-Accessories->Terminal and post the output of the following commands:

df -h

sudo fdisk -l

---

### Post by lekifsirk on 2009-12-25
kris@kris-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             109G  3.7G  100G   4% /
udev                  1.9G  304K  1.9G   1% /dev
none                  1.9G  216K  1.9G   1% /dev/shm
none                  1.9G  128K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
kris@kris-desktop:~$ 
kris@kris-desktop:~$ sudo fdisk -l
[sudo] password for kris: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61926192

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       59421       60801    11092882+   5  Extended
/dev/sda5           59421       60801    11092851   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078f93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       44749   359446311   83  Linux
/dev/sdb2           44750       60801   128937690    5  Extended
/dev/sdb5           59767       60801     8313606   82  Linux swap / Solaris
/dev/sdb6           44750       59150   115675969+  83  Linux
/dev/sdb7           59151       59766     4947988+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by lekifsirk on 2009-12-25
Thank you all for trying to help me.  I hope the info in the previous post is helpful.

---

### Post by lekifsirk on 2009-12-25
Mahngiel
I have another external hard drive and I could format it to Fat32.  Then would I install Ubuntu on it and look for files to transfer over?

---

### Post by iMisspell on 2009-12-25
> **lekifsirk said:**
> Mahngiel
I have another external hard drive and I could format it to Fat32.  Then would I install Ubuntu on it and look for files to transfer over?
I do not think that is what Mahngiel ment, just the opposite actual.

It is commen practice for people to do the following.

Install a o/s (or many operating systems) to a computer (like you have).
**OR**
Have many computers hooked up to a home network.

Have one computer **OR** one harddrive (exturnal usb, what ever (like you have)) and store all there files on that one computer **OR** one hardrive.

By doing this it make it easyer to access the pics, music, movies, document files when they are on different home computer or turn on there main computer and start it up with a different o/s (like your doing).

So, commen pratice would be to format your exturnal hardrive, find your files and move them to that exturnal drive so no matter what o/s you are using, the files will always be in the same place, your exturnal harddrive.

_

---

### Post by mikewhatever on 2009-12-26
Thanks a bunch for the output. Unfortunately, it's more puzzling then helpful, as you seem to only have multiple linux partitions, and no Windows file system is in view. Have you installed other Linux distros? Have you installed Ubuntu multiple times?

---

### Post by louieb on 2009-12-26
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61926192

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       [COLOR=Red]**59421**[/COLOR]       60801    11092882+   5  Extended
/dev/sda5           59421       60801    11092851   82  Linux swap / Solaris


```

You have huge (400+GB) of unallocated space at the start of sda - perhaps your missing partitions were once there.

Try [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") available on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  . Got to run but the testdisk wiki has excellent instuctions.

---

