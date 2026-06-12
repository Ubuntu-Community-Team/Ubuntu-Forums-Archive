---
title: "Maintaining Disks"
date: 2010-10-30
forum: General Help
---

### Post by MrJLBrown on 2010-10-30
Let's talk about disk maintenance, for a while. In Windows I had three basic tools--Disk Cleanup, Disk Defragmenter and Error Checking.

Are there Ubuntu equivalents of these operations because I like to defragment hard disks every two weeks, disk cleanup at the end of every day and Error Check at least once a month. I've seen the janitor tool which I'm wondering if it is smart enough to not delete critical system files. I know my disk has errors, the disk utility told me such but didn't offer to fix the errors. As for defragging, I haven't seen anything like that at all.

If somebody could tell me how to do these three things it would be very much appreciated.

---

### Post by baddnady23 on 2010-10-30
If I am not mistaken, with the filesystem that Linux uses, it doesn't require defragmenting.  I think the application that you are looking for is called **disk utility**.  

It is located under System>Administration>Disk Utility 

There you can run tests on your disks and verify their performance and overall conditions

---

### Post by matsuzine on 2010-10-30
There is no need to defragment a linux machine, assuming you are using the default filesystem.

Computer Janitor is intended to clean up leftover .deb files and temporary files, so it is sort of similar to disk cleanup.  You may also want to look into the bleachbit program.

Error checking is generally done as part of the boot process, every 30 boots or so.  Disk Utility is reporting errors on your disk?  What errors is it reporting?

---

### Post by Eddison on 2010-10-30
This is pretty good too..

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Eddison

---

### Post by MrJLBrown on 2010-10-31
Great that I don't have to defrag, janitor sounds reliable, but the error checking reports some bad sectors. I really wouldn't know where to begin about elaborating what is wrong with the errors. It's just as far as I know it's just telling me, "hey, we found a couple of errors on your disk." No offer whatsoever to repair them--I don't know how to repair them. Is there a tool in Disk Utility I've overlooked that fixes disk errors?

---

### Post by oldos2er on 2010-10-31
Usually bad sectors aren't fixable.

I'd be careful using Computer Janitor, don't let it mess with anything where you don't know exactly what it's doing.

---

### Post by icestation on 2010-12-29
Bad sectors are often the sign of a failing disk.  What is worse, the disk won't tell you about it, iIt will just try to fix them by marking them bad and transferring the (now possibly corrupt data) to an area reserved on the disk for sector repairs.  If this happens more than 5 times on a 100GB disk, chances are there is a problem on the horizon. There is quite an interesting article on that subject here:

[http://linas.org/linux/raid.html](http://linas.org/linux/raid.html)

What is slightly disturbing is that RAID6 and sometimes RAID10 could do a better job of protecting us from this failure mode by 

1)  Detecting it earlier and
2) Using the remaining RAID data to make intelligent decisions about which disk (and therefore which data) has gone bad (voting) and correct the right data (as opposed to randomly selecting which data to "correct").

I have a disk that has re-assigned 12 sectors and apparently dropped one.  (See attached screen shot ID 6 and ID 196).  What is more concerning is that the disk parameter ID 5 is marked RED but the disk itself is marked green in DISK UTILS.  So had I not gone into SMART tools, I would be none the wiser.
  
Solution:

1) Backup everything to tape.  Twice.  Unless you are OCD, in which case 4 times is good.
2) Nag Niel Brown (diplomatically) to enhance mdadm to address the two concerns raised above, and also raised in the article
3) Never overwrite a tape backup, just in case your data has been slowly corrupting over the years

---

