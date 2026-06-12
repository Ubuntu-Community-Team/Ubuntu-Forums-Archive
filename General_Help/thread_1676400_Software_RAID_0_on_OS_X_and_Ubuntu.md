---
title: "Software RAID 0 on OS X and Ubuntu"
date: 2011-01-27
forum: General Help
---

### Post by danielsbrewer on 2011-01-27
Hello,

I have a dual boot system with OS X and Ubuntu on a mac pro.  I would like to set up two harddrives in a software RAID 0 configuration.  I was going to set up the drives in OS X using the Disk utility, but then I was wondering whether Ubuntu would be able to read it, and how you would go about setting it up.

Thanks

---

### Post by realzippy on 2011-01-27
Ubuntu cannot "work" on a MAC software raid,since it is a *software* raid. ;-)
..you would have to install a linux (ubuntu) software raid.You could split each disc and set up an OSx softwareraid **and** Linux softraid on their own partitions.

---

### Post by danielsbrewer on 2011-01-27
That's what I feared.  I was hoping that both software RAIDs would be based on some standard or compatible in some way. Hmmmmm.

---

### Post by realzippy on 2011-01-27
Different filesystems,different kernels,no way.
But it should not be too hard:
Set up the OSx raid first not using whole discs,let there be some empty 
space on each disc,which you use for the linux software raid.

---

### Post by danielsbrewer on 2011-01-27
But if we go for RAID 0 striped then both OSs would have to know how the other system striped, so I don't know if that would work.  HFS+ is supported reasonably well by ubuntu, so the file system is not a problem.  Still not really a goer though.

---

### Post by realzippy on 2011-01-27
*....then both OSs would have to know how the other system striped...*

No.
Why?Each OS has it own 2 partitions to stripe.

---

### Post by danielsbrewer on 2011-01-27
Sorry misread your message.  It may have to be two separate RAIDs, but thats not great.  Oh well.

---

### Post by realzippy on 2011-01-27
Why not great?
There is no difference,ubuntu raid uses 2 partitions of sda and sdb,and
OSx uses 2 partitions of sda and sdb...

---

### Post by danielsbrewer on 2011-01-27
The main reason that the two partitions isn't a great solution is there would be no (easy) way to share data between the two OSs.  A common work flow for me is to work on some data in OS X and then reboot to Ubuntu and work on the same data using different software.  Also only half the space would be available to each OS.

---

### Post by psusi on 2011-01-27
It isn't great because he wants to one system to be able to access data on the other.

You can manage to get Linux to see it with some hackery involving manually building an array without superblocks and manually explaining the geometry of the raid, but that isn't the kind of thing you want to do on a daily basis.

---

### Post by realzippy on 2011-01-27
So why not a separate non-raid partiton only for sharing data?

---

### Post by danielsbrewer on 2011-01-27
Unfortunately in my particular application (bioinformatics) I am going to have very large datasets (100GB or so) where disk-reading is often the bottle neck when analysing.  RAID 0 should speed everything up.  I suppose one solution would be to have a small as possible RAID 0 space for both OSes and a non-RAID space which can be shared and just move the data in as a I need too.  That though could add as much time as not having RAID at all.

---

### Post by wentzr on 2011-04-18
danielsbrewer - 
Were you ever able to find any solution to this? I to am trying to do the same thing for multi-stream audio editing. 

I'm going to really dig on this, if I'm able to find a solution I'll post it back here. 

-Rob

---

### Post by danielsbrewer on 2011-04-19
It seems that software RAID is implemented differently in the different OSs, so that they are incompatible.  So I could not find any possibility of sharing software RAID between Linux and OS X.  Hardware RAID would be fine, but it is far too expensive for me.  If you find anything I would be very pleased to hear about it.

---

