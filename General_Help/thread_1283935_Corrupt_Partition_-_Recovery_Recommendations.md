---
title: "Corrupt Partition - Recovery Recommendations?"
date: 2009-10-06
forum: General Help
---

### Post by graaant on 2009-10-06
Hey guys,

So I have a 1TB External HDD that I was trying to change from NTFS to FAT32. I split the HDD into 2 partitions and copied all my data from the NTFS partition to the FAT and then I deleted the NTFS partition and "grew" the FAT partition.

I let it run for hours, only to be greeted with an error! :(
This is when I discovered that all my data had become corrupt! :(

File names, extensions and even file types are pretty much gone, all names are now random characters and I can't open any of the folders. I've noticed there's a few random files that are pretty big and I'm hoping they're holding some of my data.

I'm scanning it with Advanced Partition Recovery at the moment, but I'm not liking my chances. I've tried to run a CHKDSK through it but it tells me it can't run on a RAW partition?
I'd really like to get this data back, as it had most of my music, movies and quiet a bit of work data.

Has anyone encountered this before or know of ANY way to recover this? Any suggestions would be greatly appreciated.

---

### Post by dragos240 on 2009-10-06
Testdisk is awesome.

---

### Post by graaant on 2009-10-06
> **dragos240 said:**
> Testdisk is awesome.

I'll give it a try. Thanks.

---

### Post by earthpigg on 2009-10-06
> **dragos240 said:**
> Testdisk is awesome.

+1.

google the wiki.
testdisk also includes photorec. google that wiki, and use photorec first without actually changing anything on the drive.

---

### Post by graaant on 2009-10-06
YAYYY!
I got it back!
That is amazing!

It's copying over now, hopefully it'll be alright once it's done.

Thankyou so much guys! :D

---

### Post by JillSwift on 2009-10-06
For anyone stumbling across this thread later: Remember the three pillars of computing:

[LIST=1]
[*]Backup
[*]Backup
[*]Backup
[/LIST]

---

### Post by hessiess on 2009-10-06
FAT has no redundancy and gets corrupted very easily, only use it if there is no other option.

---

### Post by frodon on 2009-10-06
Moved to General Help forum.

---

