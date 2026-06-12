---
title: "Clonezilla Backup Issue"
date: 2012-10-09
forum: General Help
---

### Post by hawk007 on 2012-10-09
Hi, i followed this video on youtube and created a backup, all seemed ok. Heres more info:

Server dl380 running ubuntu server 12.04
Raid 1 mirroring over 6 SCSI HDs
I believe a total of 4.2 GB has been used.
I have installed lamp-server

At this point i created a backup using this video as a guide:

[http://www.youtube.com/watch?v=T7ywkc4LU10](http://www.youtube.com/watch?v=T7ywkc4LU10)

The backup was approximately 355MB (that seemed rather small)

I then changed the default apache index file from IT WORKS to "It Works! Thank Heck"

I then restored after which the default apache index page didnt return to IT WORKS and still reads "It Works! Thank Heck"

So the restore didnt work, or even the backup didnt work.??

Any guidance in this would be apreciated thanks.

PS. as in the video i restored "IN PARTS" and "THE WHOLE DISK" but still the apache page didnt change.

Im using the "clonezilla-live-1.2.12-67-i686-pae" ISO version. I tried the ubuntu but that wouldnt move through any of the process after choosing the basic settings. Didnt recognize LVM settings.

---

