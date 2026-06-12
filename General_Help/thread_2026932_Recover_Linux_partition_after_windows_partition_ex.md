---
title: "Recover Linux partition after windows partition expanded over it."
date: 2012-07-16
forum: General Help
---

### Post by JamezQ on 2012-07-16
So, I was trying to give windows some more space on the drive. And it seemed as though there was free space between windows and linux, and so I went in windows, and had it expand to take up that space.

I then immediately restarted, so windows does not over write linux data just in case it did expand over it.

And my fears were confirmed, grub was not able to boot and gave an error of "partition not found".

Before I did this, I did backup the windows partition with dd. But not the linux one.

I am currently backing up the drive to a .img file to try to recover it all.


So, I have tried testdisk, sadly it only see's windows. I used supergrub2 to boot, and it was able to boot into windows, but not linux.

I had my linux swap in an extended partiton, and I thought I had my ext4 fs right next to it, but I guess I was wrong.


I made a stupid mistake, not backing up both linux and windows. 



So, any suggestions? I will have the .img files, so don't worry about me loosing my data, as we will be working on backups. 

I do (because I used dd first) have the *exact* size of the old windows partition, so maybe that can help.

I'm not afraid to google or read, and I can get dirty with good ol' command line linux utilities. Tell me whatever you think will help.

---

### Post by oldfred on 2012-07-16
Did you do the deeper search in testdisk, as it usually finds old partitions? If you know partition start info you may be able to manually rebuild it, but I think it really works the same as testdisk.

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)


I always suggest only using Windows partition tools to shrink Windows and use Linux tools for Linux partitions. But I guess you have to use Windows to expand also as it has to have the correct partition start & size in the partition boot sector that matches the partition table.

If testdisk does not work, you may have to reinstall Ubuntu. You can use photorec to scan LInux partition for any data files you did not back up. I have used photorec. It is a long slow process, only finds files by type since partition table is missing and it is only searching for file header info. For some text files I had saved many times and wanted to recover, it found every old copy. I had an old backup, compared many of the recovered versions, but never was sure I found last saved one. Lots of work grepping & comparing files.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by JamezQ on 2012-07-19
I already recovered all the files I could using photorec.

------------------------------------------
While testdisk seems to find ext3 partitions, I can't list files from them, it always says the file system seems to be damaged.

Would it be possible to mount them if they were restored?

Also, maybe relevant, I always get these errors during fdisk.


root@ubuntu:~# fdisk -lu
fdisk: unable to seek on /dev/sda: Invalid argument

And when using parted 

(parted) unit s                                                           
(parted) rescue
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? i                                                    
Error: Invalid partition table on /dev/sda -- wrong signature b76d.

-------
Test disk can, however, list files from the ntfs partition


-----------------

output of sfdisk -l

```
Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 48966183 does not have an msdos signature
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  18703-  18704- 150239444+   7  HPFS/NTFS/exFAT
/dev/sda2      18704   35112-  16409- 131805198    f  W95 Ext'd (LBA)
        start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      18704+  19456     753-   6048441   82  Linux swap / Solaris
        start: (c,h,s) expected (1023,254,63) found (1023,1,1)

```

---

### Post by JamezQ on 2012-07-19
Here is an image of the completed testdisk deep search.


[IMG]http://i.imgur.com/ZJCqt.png[/IMG]

I think, for the sake of safety, (and because each new deep search takes 3 hours) I will wait at this screen, for now.

Is it possible to restore the partitions even if testdisk cannot list the files? Or ideally, can I somehow mount them without writing the partition to the disk?

I would like to backup the linux partition, and then install 12.04 on the computer, so far I have been sitting on a live cd for about 3 days.

---------------------

I really appreciate your help, you're awesome.

---

### Post by oldfred on 2012-07-19
Testdisk uses CHS which can be translated to sectors which everyone else uses.

Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

But from what I see, many start & ends overlap. Without knowing which is the version you may want to try to salvage I cannot suggest.

---

### Post by JamezQ on 2012-07-19
Well luckily I did a dd backup of the partition, so I can test them all.

---

