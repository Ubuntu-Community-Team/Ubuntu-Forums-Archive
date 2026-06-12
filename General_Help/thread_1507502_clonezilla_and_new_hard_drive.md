---
title: "clonezilla and new hard drive"
date: 2010-06-11
forum: General Help
---

### Post by elj4176 on 2010-06-11
Tried to restore an image of a 60GB laptop drive to a new 160GB laptop drive. After the restore the 160Gb drive is now only showing 60Gb - just like the old one. I have tried everything I can think of including deleting all of the partitions but it still says it is only 60GB.
How can I fix this?

---

### Post by labinnsw on 2010-06-13
Have you tried to resizing the partition using the live CD and Gparted? You will be amazed.

---

### Post by elj4176 on 2010-06-26
I have tried that. The drive thinks it is only 60GB. It is in fact a 160GB drive. Gparted shows a 54.5GB unallocated partition table. If I wipe the drive and restart gparted it still sees the drive as 60GB. The dropdown where you can select which drive to work with shows 60GB for that drive.

Somehow when I cloned the 60GB drive to the 160GB drive Clonezilla made the 160GB drive think it is only 60GB. 

My next thing to try is Dereks boot nuke. If that doesn't fix it then I may just send the drive back as faulty and hope they replace it.

---

### Post by elj4176 on 2010-06-29
Here is the problem better explained:

[http://www.goodells.net/dellrestore/hpa-issues.htm](http://www.goodells.net/dellrestore/hpa-issues.htm)

I'm now trying to copy just the XP partition to the new drive. I figured out how to recover the 'lost' space on the drive using HDAT2 by setting the LBA to 24 instead of 48 and setting to max capacity. 

If (when) I figure this out I will post an update in case anyone else runs into this nonsense.

---

### Post by dino99 on 2010-06-29
you can use these tools from [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by elj4176 on 2010-07-01
Thanks for the link but those do not address my problem. The deal with a bad drive or deleted files/partitions. I have used both of those previously with great results though.

I finally gave up and just reinstalled a fresh copy of XP on the new drive and then moved the files I needed to keep from the 60 GB drive. After googling and trying several different approaches and wasting a lot of time I had to cut my losses.

---

