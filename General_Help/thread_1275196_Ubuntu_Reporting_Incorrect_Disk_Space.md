---
title: "Ubuntu Reporting Incorrect Disk Space"
date: 2009-09-25
forum: General Help
---

### Post by bgilbert on 2009-09-25
Hi,

I recently stumbled upon this issue after deleting about 30 gigs of data off of my laptops 250gb hard drive. I checked my hard disk free space via system monitor after performing the delete and was surprised to not see much difference in the free space reported.

I've run two separate programs...Disk Usage Analyzer and kDirStat, both of which report only about 50gb of space currently being used with a total of about 224gb of disk space. However Ubuntu is currently only reporting 94gb of free space. To add to the confusion Disk Usage Analyzer only lists 50gb as being used out of the 224gb on my hard disk, but on the same page shows the used amount as being 118gb with 105gb free. 

This is some pretty confusing stuff and I've tried searching for similar issue, but have found none. Does anyone have an explanation for the results that I am seeing?

BTW, I've attached a shot of the Disk Usage Analyzer screen and one of the System Monitor.

Thanks in advace!
-Bryan

---

### Post by Liolikas on 2009-09-25
Those programs are nice looking but little confusing try to paste simple:
sudo fdisk -l
output here we will see things well.

---

### Post by bgilbert on 2009-09-25
Thanks for your response. The output from the fdisk -l command is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x986ec530

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29507   237014946   83  Linux
/dev/sda2           29508       30401     7181055    5  Extended
/dev/sda5           29508       30401     7181023+  82  Linux swap / Solaris

---

### Post by bgilbert on 2009-09-28
Bump?

---

### Post by StuartN on 2009-09-28
> **bgilbert said:**
> Bump?

It sounds like your trashcan needs emptying - your figures would be about right. In Gnome it would be a right-click on the trash-can icon in the bottom right and then Empty trash.

Otherwise the output from **df** might help.

---

### Post by bgilbert on 2009-09-28
Thanks for your reply....Here is the output for df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            235147096 124460512  98835840  56% /
tmpfs                  1860428         0   1860428   0% /lib/init/rw
varrun                 1860428       232   1860196   1% /var/run
varlock                1860428         0   1860428   0% /var/lock
udev                   1860428       172   1860256   1% /dev
tmpfs                  1860428       372   1860056   1% /dev/shm
lrm                    1860428      2192   1858236   1% /lib/modules/2.6.28-15-server/volatile

I see that this is reporting a similar value to System Monitor...I'm just confused as to where this all this used space is coming from. My trash bin has been emptied, and I still can't find any programs that give a file system usage breakdown that shows that I have more than around 50gb of used space on the file system.

---

### Post by CatKiller on 2009-09-28
> **bgilbert said:**
>  I recently stumbled upon this issue after deleting about 30 gigs of data off of my laptops 250gb hard drive.

If you deleted it as root, it may well be in root's Trash. That won't show in baobab (Disk Usage Analyser) when run as a normal user since you don't have permission to read root's Home folder. A file browser window run as root should sort you out.

```
gksudo nautilus
```

---

### Post by bgilbert on 2009-09-28
Thanks a lot for your response...that solved my problem! 

I ran sbackup several times before, and I thought that I had run it against an external hard drive and that it was just not working. However, I found that it was actually backing up my files under /var/ with root permissions assigned. I found that there were about six of these backups by running 'baobab' under root.

Thanks again for your response!

---

### Post by 3rdalbum on 2009-09-28
Also note that some utilties will count the space used in /media, ~/.gvfs and /sys, which is incorrect because files and folders in those places are not actually stored on your hard disk.

---

