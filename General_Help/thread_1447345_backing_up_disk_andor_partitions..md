---
title: "backing up disk and/or partitions."
date: 2010-04-05
forum: General Help
---

### Post by Tom_T on 2010-04-05
Hi

I'm looking for some advice on backing up my computer.

I currently have Ubuntu, XP Pro & XP Home installed as a Triple boot.
So I'm looking for a good way to back this up. 

Ideally I'd like to be able to backup the entire disk, but have the ability to restore the full disk or specific partitions etc.

I have tried Clonezilla in the past, but it always failed on restore.

Would I be better buying True Image or Ghost, or is there an other solution ?

Thanks :)

---

### Post by kblft on 2010-04-05
you could just try straight copying the entire disk 

there's actually a pretty good guide in the forums 

[http://ubuntuforums.org/showthread.php?t=786410](http://ubuntuforums.org/showthread.php?t=786410)

---

### Post by warfacegod on 2010-04-05
The last time I checked Norton Ghost had some major issues with ext filesystems. Like breaking them.

You might try Remastersys.

---

### Post by john newbuntu on 2010-04-05
Not sure on what problems you had with clonezilla.  I have used it once without any problem in restoring a partition.
Well, you could try partimage or the dd_rescue command to backup and restore from liveCDs.  Personally I have not tried these.

---

### Post by Tom_T on 2010-04-05
Thanks for the suggestions.

Any others to look at ?
Cheers

---

### Post by warfacegod on 2010-04-05
[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by frenard on 2010-04-10
There is a backup software, Arkeia Network Backup, available in LTS repository, free to Ubuntu users (up to 2 machines backed up, including Linux, Windows or Mac OS X).

Information for download are at [http://www.arkeia.com/ubuntu](http://www.arkeia.com/ubuntu)

Fred

---

### Post by joel@parke.ods.org on 2010-07-12
Hi,

I have installed arkeia and run my first backup.  When attempting to restore a few files as a small test.  I discover that some of the files are missing and the backup seems about 1/2 the size it should be.  Has Anyone had success with arkeia?  

THANKS!

---

### Post by frenard on 2010-10-19
It is not surprising that the data volume is less on the destination (disk or tape) as data are compressed before being sent to the backup server.

Regarding missing files, it might be because there is a file-type exclusion (you can say: skip tmp or whatever extension file-type)?

Hope it helps,

Fred (from Arkeia)

---

