---
title: "big issues with &quot;no space left on device&quot;!"
date: 2009-07-24
forum: General Help
---

### Post by bootdoc on 2009-07-24
What is up with the no space left on device error!  I have 19 gigs for / and 212.86 gigs for /Home.  When I run disk usage analyser (scan file system) it shows / 100% and /Home 56%.  When I scan individual folders in / they all come back 100%.  Then I go check the properties of the offending folders i.e. /dev/shm has 1 item at 64mb with 992mb free space.  How is it that all top level folders are 100%.

Now the /home shows 56% on the file system scan but when I run scan folder on just the home part. it shows 100%.

I have moved and deleted files and folders, and run apt-get clean but nothing changes.

My / is ext4 and /home is ext3.

fdisk -l shows:
sudo fdisk -l
[sudo] password for charlie: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c5a60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         124      995998+  83  Linux
/dev/sda2             125       30401   243200002+   5  Extended
/dev/sda5             125       27911   223199046   83  Linux
/dev/sda6           27912       30401    20000893+  83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9561    76798715+  83  Linux
/dev/sdc2   *        9562       19457    79488352    b  W95 FAT32

 $ df shows:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             19686804  19046216         0 100% /
tmpfs                  1017476         0   1017476   0% /lib/init/rw
varrun                 1017476       224   1017252   1% /var/run
varlock                1017476         0   1017476   0% /var/lock
udev                   1017476       168   1017308   1% /dev
tmpfs                  1017476       712   1016764   1% /dev/shm
lrm                    1017476      2560   1014916   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda1               980308     82904    847608   9% /boot
/dev/sda5            219696776 121406500  87130324  59% /home
overflow                  1024        20      1004   2% /tmp
/dev/sdc1             76194916  72095156    259764 100% /media/disk
/dev/sdc2             79449536  72694128   6755408  92% /media/disk-1

df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext4     19G   19G     0 100% /
tmpfs        tmpfs    994M     0  994M   0% /lib/init/rw
varrun       tmpfs    994M  228K  994M   1% /var/run
varlock      tmpfs    994M     0  994M   0% /var/lock
udev         tmpfs    994M  168K  994M   1% /dev
tmpfs        tmpfs    994M  712K  993M   1% /dev/shm
lrm          tmpfs    994M  2.5M  992M   1% /lib/modules/2.6.28-14-generic/volat

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G   19G     0 100% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  228K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  168K  994M   1% /dev
tmpfs                 994M  712K  993M   1% /dev/shm
lrm                   994M  2.5M  992M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda1             958M   81M  828M   9% /boot
/dev/sda5             210G  116G   84G  59% /home
overflow              1.0M   16K 1008K   2% /tmp
/dev/sdc1              73G   69G  254M 100% /media/disk
/dev/sdc2              76G   70G  6.5G  92% /media/disk-1

what needs to be done to get things working properly?

---

### Post by Johnny B on 2009-07-24
whatever folder you scan will always be 100% of itself
this is not showing free space, its showing how the used space is distributed
(with disk usage analyzer)

you should scan / and find out whats using all that space

---

### Post by Maheriano on 2009-07-24
Maybe not your issue but I've deleted files off a flash drive before and they would disappear from the file manager interface but would actually go to the recycle bin. They're not actually deleted from the device yet, or their pointers aren't. So I remove the flash drive, files are still in the recycle bin, plug the drive into another computer and it shows as full. But there's still no files showing on it.

---

### Post by drs305 on 2009-07-24
I wrote a guide on finding why a partition 'suddenly' becomes full. The link is "DiskSpace" in my signature line.

The 3 most common reasons are undeleted trash (your's and root's), large log files, and backups which were supposed to be made to a different partition or external device that were copied to / (usually) because the backup device wasn't properly mounted at the time.

---

### Post by bootdoc on 2009-07-24
thanks for the replies.  I just reinstalled and ran disk usage analyzer again and it still shows / at 100%.  BUT WAIT!

$df 

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             19686804   6821496  11865264  37% /
tmpfs                  1017476         0   1017476   0% /lib/init/rw
varrun                 1017476       224   1017252   1% /var/run
varlock                1017476         0   1017476   0% /var/lock
udev                   1017476       168   1017308   1% /dev
tmpfs                  1017476       700   1016776   1% /dev/shm
lrm                    1017476      2560   1014916   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1               980308     50424    880088   6% /boot
/dev/sda5            219696776 121364828  87171996  59% /home
/dev/sdc1             76194916  72095156    259764 100% /media/disk
/dev/sdc2             79449536  72694128   6755408  92% /media/disk-1

I guess i don't understand the disk usage analyzer utility.

---

### Post by drs305 on 2009-07-24
> **bootdoc said:**
> I guess i don't understand the disk usage analyzer utility.

The top of disk usage analyzer will always show 100%. You might find the System Monitor or *gparted* graphics more understandable. System, Administration, System Monitor, File Systems tab. Make sure you expand it far enough right to see the "used" section.

Of course, gparted and System Monitor only show you the free space of the the total partition and not individual folder sizes. 

There is a section of the guide linked in my signature line on how to intrepret what DUA is displaying if you haven't looked at it. Johhny B above explained why it shows 100% but perhaps the guide explains it differently.

---

### Post by bootdoc on 2009-07-24
thanks drs305.  I read your guide.  very helpful.  Right now after reinstall and upgrade df shows / at 41%  It will be interesting to see if that changes in the near future.  I pretty much have the system back to where is was before.  Only diff is I have not removed openoffice ubuntu vers. and installed the full version.

---

### Post by drs305 on 2009-07-24
> **bootdoc said:**
> thanks drs305.  I read your guide.  very helpful.  Right now after reinstall and upgrade df shows / at 41%  It will be interesting to see if that changes in the near future.  I pretty much have the system back to where is was before.  Only diff is I have not removed openoffice ubuntu vers. and installed the full version.

Sorry that you weren't able to discover what took up the space before you reinstalled but glad you have the free space back nevertheless. 

Monitor your free space and if it shrinks considerably try running through the guide's steps to see if you can isolate what is causing the problems. That's one thing about computers, they do what they are told, and if nothing has changed the problem may return. Hopefully not. ;-)

If there were things in the guide you didn't understand I'd be glad to help you out with them.

---

### Post by Martiini on 2010-03-04
Does anyone know what is default ubuntu installation size? Something around 2gb?

What I currently have is:
```

martin@hpubu:~$ df -h | egrep /$
/dev/sda5             4.9G  4.4G  263M  95% /
martin@hpubu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.9G  4.3G  268M  95% /
none                  937M  292K  937M   1% /dev
none                  944M  128K  944M   1% /dev/shm
none                  944M  228K  944M   1% /var/run
none                  944M     0  944M   0% /var/lock
none                  944M     0  944M   0% /lib/init/rw
none                  4.9G  4.3G  268M  95% /var/lib/ureadahead/debugfs
/dev/sda6              78G   71G  7.4G  91% /media/stuff
martin@hpubu:~$ 

```

---

### Post by plucky on 2010-03-04
> **Martiini said:**
> Does anyone know what is default ubuntu installation size? Something around 2gb?

What I currently have is:
```

martin@hpubu:~$ df -h | egrep /$
/dev/sda5             4.9G  4.4G  263M  95% /
martin@hpubu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.9G  4.3G  268M  95% /
none                  937M  292K  937M   1% /dev
none                  944M  128K  944M   1% /dev/shm
none                  944M  228K  944M   1% /var/run
none                  944M     0  944M   0% /var/lock
none                  944M     0  944M   0% /lib/init/rw
none                  4.9G  4.3G  268M  95% /var/lib/ureadahead/debugfs
/dev/sda6              78G   71G  7.4G  91% /media/stuff
martin@hpubu:~$ 

```

**About 3.5G.**

This is my / partition after 5 months > /dev/sda1              20G  4.2G   15G  23% / but I have a separate /home partition ,which you do not,so all your configuration files are loaded onto your / partition.

---

