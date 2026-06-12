---
title: "Simple back up tar crash in maverick"
date: 2011-01-25
forum: General Help
---

### Post by nacho-wan on 2011-01-25
Hello people:

I have been all morning trying different backup programs: dejavu, backintime and now simple backup. I really liked this last one because it not only backs up the home directory but also critical parts of the file system (var, usb, etc).

However I have been unable to make it work. As my configuration, my back-up is about 36Gb+ and should go to a external fat32 drive (a WD passport 300GB btw). Since the drive is fat32 -with a file size limit of 4Gb- my backup can't be made in a single compressed file. 

So I configured sbackup to not compress and chunk the backup in 4Gb bits (fat32 setting). However every time I run the backup I got: An error occurred Unable to finish successfully. TAR terminated with errors.

I read in launchpad that this was due to sbackup requiring a new version of tar, so I downloaded natty's deb file and installed it. But it keeps generating the same error.

Does anybody have been able to run sbackup in maverick with settings similar to me. If so how?

---

### Post by Fire_Chief on 2011-01-25
Is it out of the question to reformat the USB drive to use another filesystem such as EXT3, EXT4, or NTFS? That would provide a more robust filesystem to handle the backup anyway and also eliminate the need to chunk the backup uncompressed. Just a thought.

Cheers!

---

### Post by nacho-wan on 2011-01-25
I could do that, but I'm not sure if I could safety format a flash based drive like the Western Digital Passport I have

---

### Post by Fire_Chief on 2011-01-25
Sure you can. It behaves just like a regular drive for the purposes we are discussing here.

Though you should copy off anything you want to keep before the reformat.

Then unmount the drive and open the Disk Utility tool from System -> Administration -> Disk Utility
Select the USB drive in the left pane and click on Format Drive in the right pane. Choose your options and go. :)

Cheers!

---

### Post by nacho-wan on 2011-01-26
Thanks Fire Chief. I had that doubt from a long time. That could be a solution to my problem, still I'm going to leave the thread open a little while to see if somebody was able to make work sbackup as it should.

---

### Post by juky on 2011-02-22
Hi all,

I have a similar issue. So same error occurred with TAR.
However my HW config is a bit different:

Partitions:
Filesystem (where OS resides) is 20 Gb ext4.
Data (for storing Data) is 85 Gb, also ext4.

Anyone else had similar issue? Tried to search through my best friend Google :-) but nothing which makes sense popped out.

Thanks,
juky

---

### Post by nacho-wan on 2011-02-22
Did you get an error message? Can you post it here.

---

### Post by juky on 2011-02-23
> **nacho-wan said:**
> Did you get an error message? Can you post it here.

Attached complete log.
I am backuping entire disk ( "/" specified in "Includes" part).

Parts which are definitely strange to me:

> 2011-02-22 10:25:19,987 - INFO in profile_handler.__collect_files(236): Summary of backup
2011-02-22 10:25:19,988 - INFO in profile_handler.__collect_files(237): Number of directories: 0.
2011-02-22 10:25:19,988 - INFO in profile_handler.__collect_files(238): Total number of files: 0.
2011-02-22 10:25:19,988 - INFO in profile_handler.__collect_files(239): Number of symlinks: 0.
2011-02-22 10:25:19,988 - INFO in profile_handler.__collect_files(240): Number of files included in snapshot: 0.
2011-02-22 10:25:19,988 - INFO in profile_handler.__collect_files(241): Number of new files (also included): 0.
2011-02-22 10:25:19,989 - INFO in profile_handler.__collect_files(242): Number of files skipped in incremental snapshot: 0.
2011-02-22 10:25:19,989 - INFO in profile_handler.__collect_files(243): Number of items forced to be excluded: 0.
2011-02-22 10:25:19,989 - INFO in profile_handler.__collect_files(244): Number of items to be excluded by config: 0.
2011-02-22 10:25:19,989 - INFO in profile_handler.__collect_files(245): Maximum free size required is '0 MiB 0 KiB'.

Maximum free size required 0 MiB 0 KiB?!?? Also files, symlinks and directories included is equal to "0"?!?!

 Probably this wrong reading of what should be backed up is causing TAR issue later on.

Any help appreciated.
Thanks,
juky

---

### Post by nacho-wan on 2011-02-23
Well, maybe is about permits. Do you get a password promt when running simple back up. Normal users can't touch the entire filesystem. 

Also, you might consider an alternative back-up utility. Currently I'm using Back in Time. Look for it in the software center by searching for back-up. Just remember to run it as root.

---

### Post by juky on 2011-02-24
> **nacho-wan said:**
> Well, maybe is about permits. Do you get a password promt when running simple back up. Normal users can't touch the entire filesystem. 

Also, you might consider an alternative back-up utility. Currently I'm using Back in Time. Look for it in the software center by searching for back-up. Just remember to run it as root.

Well,I do not know if its about permits. I have tried to log in as root and run it, but its quite the same.
I have already backed it up with tar ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), did quite a good job for me.
Will post back if I made it with Simple Backup.

---

### Post by pavelzag on 2011-04-20
Hey guys, I wanna bump it up as I am having the same issues myself.
Using tar 1.25 with a NTFS drive.
Should there be problems?

---

### Post by AhmadSharifi on 2012-01-09
Well, finally I found a decent solution for this problem and here I share it with you. The first  problem is that sbackup configuration should be set by the root. This is what I did and I recommend, open a terminal and type:
```
gksu sbackup-config-gtk
```
now go to destination section and choose your backup directory as default destination. Right now, you can run sbackup restore tool by following code as root:
```
gksu sbackup-restore-gtk
```
maximize the window and restore your backups, the problem never dare to appear again.:-)
Good luck.
Ahmad.

---

