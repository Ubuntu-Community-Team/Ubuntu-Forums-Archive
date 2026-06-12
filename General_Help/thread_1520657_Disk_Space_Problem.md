---
title: "Disk Space Problem"
date: 2010-06-29
forum: General Help
---

### Post by ajberri on 2010-06-29
First off, hi!

I'm running a server on Ubuntu with two partitions. One for the filesystem, which reportedly has 70gb of space, and one for a media directory with 140gb of space. Recently the filesystem is reporting 0 kb of available space (I even deleted about 30MB of log files, and still saying 0kb).

Can't start the mysql service as there is no space (this is how I first became aware of it). 

I ran the disk usage analyzer, and it reported that only 3/70 gb or so were being used by the filesystem, and the rest being taken up by media. Is there any reason why the media directory would also be on this partition? Are files being duplicated or? I rick click on media, and it says there is 90gb available space. Right click on filesystem, 0.

---

### Post by drs305 on 2010-06-29
You found one reason for full disks - log files. Other common reasons are undeleted trash (trash takes up space until the Trash bin is emptied - in GUI at least) and backups made to the wrong partition. If a backup is made to a mountpoint, but the backup partition isn't mounted at the time, the backup can be made to the /system partition.

Here is a guide I wrote a while back about analyzing disappearing disk space. I'd consider the "wrong mount point" possibility first although there are of course other things to explore as well.

[ HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by ajberri on 2010-06-29
The logs folder is quite small, trash bin is empty. That isn't the problem.

There should be 70gb of space on the filesystem partition, which is ample. The main problem as I see it is the media folder (which **should** be on another partition) is reported as being on the filesystem partition. i.e. it's on **two** partitions (evidenced by the fact that when I go in to the folder and view the properties, it reports 90gb of free space).

---

