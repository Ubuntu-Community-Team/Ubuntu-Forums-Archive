---
title: "Backing Up"
date: 2006-04-27
forum: General Help
---

### Post by cssutto on 2006-04-27
What should I use to back up a dual boot system with Ubuntu and WK2?

Can one backup utility back up both?

CSSJR

---

### Post by Sef on 2006-04-27
> What should I use to back up a dual boot system with Ubuntu and WK2?

If your just backing up files, then a cd-rw or dvd-rwwill do fine.   If you want to back up programs as well, then you will need a external hard drive.

> Can one backup utility back up both?

No, it can't.  You would need two programs, even if they were made by the same company.

---

### Post by cssutto on 2006-04-27
I was asking about the proper utility, hopefully one that would back up the entire hard drive including both OS.

I have the external Maxtor, which I use to back up W2K.

I will have accounting records to back up from W2K for some time, as it is not going to be easy to change that over to linux.

CSSJR

---

### Post by cgjones on 2006-04-27
If you are interested in doing a full system backup, take a look at Norton Ghost. With Ghost, you could create a complete drive image, and it would work with both Windows and Linux, provided that the Linux partitions are EXT2 or EXT3. There are also similar open source offerings available.

---

### Post by justleen on 2006-04-27
you can use DD as wel to create a full disk image..

---

### Post by cssutto on 2006-04-27
I used Ghost and despised it.

I would hope for something more user friendly and more reliable.

For the past few months, I have been using XXClone for W2K.  I like it because you can go directly to the file on the external and read the file just as though it is on the hard drive.  

I would like t have something similar that can be run from Ubuntu and hopefully one that can do a mirror image on one schedule and back up individual files on a different schedule.

What I see from running a quick short search of the subject is that backing up under linux is every bit as lacking as it is under W2K.

CSSJR

CSSJR

---

### Post by cssutto on 2006-04-27
I am obviously new to linux, so I have to ask why not tar?

My understanding that is what tar was originally designed to do.

I seems to me that tar with a few conditions should do it.

But probably not anything in the W2K partitions.

CSSJR

---

### Post by cgjones on 2006-04-27
It really depends on exactly what you want to backup. Are you looking at doing just data backups, or more of a full system backup that you can restore from?

---

### Post by cssutto on 2006-04-27
As stated above, both.

I would like the mirror image say once a week and data every night at a certain hour to be started by cronn, which I use on W2K.

CSSJR

---

### Post by cgjones on 2006-04-27
Here are some links that might help with the drive image.
[Partimage]("http://www.partimage.org/")
[Drive Image Utilities]("http://www.pccitizen.com/driveimage.htm")

As for data backups, is it a local or remote backup?

---

### Post by cssutto on 2006-04-27
Local

---

### Post by cgjones on 2006-04-27
Since it is local, I would look into rsync, or just write a script that tar's up the data and copies it to the backup directory.

---

