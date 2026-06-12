---
title: "Backup system to NTFS or refomat partition?  Size?"
date: 2012-06-23
forum: General Help
---

### Post by Rob Sayer on 2012-06-23
Day 5 of Linux .... :guitar:

I want to backup the system ... I'm storing all my data on Desktop, I prefer to install the apps I want & configure the system the way I want it and back the system and data separately.  It's single boot 12.04.

All my external backup HDs are NTFS.  Fine for data.  For linux system backup I'm not so sure.

So I'm thinking I may want  repartition / rearrange my old Windows 7 backup space (no longer needed for that computer) in Windows and use some Ubuntu tool to reformat.

Question ... which format ... although from this sudo fdisk -lu:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc1e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482639871   241318912   83  Linux
/dev/sda2       482641918   488396799     2877441    5  Extended
/dev/sda5       482641920   488396799     2877440   82  Linux swap / Solaris

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16     7813119     3906552    b  W95 FAT32

I'm guessing fat32?

Should I do the reformat from Ubuntu or in Windows?  And, if Ubuntu, what tool?

Also, I don't really know how much backup space is needed for just the system, excluding data.

Thanks in advance ...

---

### Post by oldfred on 2012-06-23
I do not recommend FAT32 for anything other than where required for Camera or other external type devices. NTFS has a journal (for recovery) and can store files over 4GB. I lost a lot of backups (fortunately did not need them) as I was backing up to FAT32 and it was alway 4GB. 

Also if you copy files from Linux to Windows format you lose permissions and ownership. That is ok for most data, but not system files.

 discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I just have home system and backup with rsync my important data and also copy the most important data to DVDs periodically.  I plan just to reinstall and restore /home and my data but see no need to back up system as the only difference then is built up histories like log files that expand system backup. I do try to backup any system settings I may change & list of installed applications.

I use gparted for all changes to partitions, formats & sizes. But if changing Windows 7 or Vista use the Windows tools to shrink the Windows partition, but not to create new partitions. It may convert to dynamic partitions which you do not want.

---

### Post by cool110 on 2012-06-23
If you think there's enough space for both backup sets  install gparted to resize the existing partition and make a new one. If you just want to reformat the entire disk you can do it in disk utility.
In both cases use one of the ext filesystems,

---

### Post by Rob Sayer on 2012-06-24
OK, I guess I need to get better used to how the log files and such work.  Thanks.

But I'd still like to treat data backup separately and keep separate backups of OS and application programs installed.

Since I don't really know how much space I need, what's the approximate size of a 12.04 64 bit install without any other programs installed?

---

### Post by oldfred on 2012-06-24
A full install is between 4 and 5GB. They say 4.5GB required, but as more updates take place it grows. Much of that can be housecleaned which you might want to do before backing up.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

But I find any full image gets old and I do not do it often enough.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
I added a few things to my backups:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Rob Sayer on 2012-06-24
Great info & links.  Thanks!

---

