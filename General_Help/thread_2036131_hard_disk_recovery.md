---
title: "hard disk recovery"
date: 2012-08-01
forum: General Help
---

### Post by xachu4u on 2012-08-01
I have WD elements 500 GB hard disk. It had a lot of my important files stored in it.

By mistake my friend deleted the partition in the disk, while using disk utility(atleast thats' what i think had happened).

Now the hard disk will not be detected in windows or linux..
Only disk utility says that i have attached the hard disk.

I really need the data that was in my disk.
The only option i can think of is to format the disk in NTFS format and use some recovery tool.I don't know of any effective recovery tool in linux.

I am also thinking along this line: since only the partition was deleted, there must some quick fixes available...
LINUX GEEKS ....help me....:KS

---

### Post by Ubun2to on 2012-08-01
What was the filesystem on it before the partition was wiped? That can help us determine what recovery programs are available for you to use.
Also, to prevent this from happening again, remember to keep your friends from messing with your partitions unless you are monitoring them.
Don't attempt to edit anything on there. Don't save any files, don't make any backups, nothing. If you try and edit anything or write anything, that will overwrite the old files on there. A hard disk is never truly wiped until you overwrite it with data-it just becomes unlisted. Once it has been written over, however, it is gone.
If the filesystem is NTFS, if you have a Windows machine, you can try recovery via command prompt, but it's been awhile since I did that last, so I forget how.

---

### Post by xachu4u on 2012-08-01
thanks...i will keep that in mind.

the hard disk had ntfs file system....

---

### Post by xachu4u on 2012-08-01
Is that the only solution...
well iam going to try it ...

---

### Post by rich1842 on 2012-08-01
If you have kubuntu you will have access to KDE Partition Manager and there is a restore option there but take great care!

There is also gparted available with ubuntu, or you can download a live disk version of that. You boot into gparted live and there are rescue and recovery options there.

These will work with NTFS. 

At the WD website you can download a 'Data Lifeguard for Windows' - a rescue software for their drives. You install as software, see if you can see your drive.

Post back for more help.

---

### Post by Mark Phelps on 2012-08-01
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by Grenage on 2012-08-01
> **Mark Phelps said:**
> 5) Run GetDataBack and select the option to find Deleted files.

I've used GDB for NTFS, and will testify to its quality; it's one of, if not the best.

---

### Post by xachu4u on 2012-08-07
this is what i finally did...hope it helps others in future.


I took my harddisk to my friend who had Windows7, formatted it in NTFS giving a blank 500 GB hard disk.

[http://www.easeus.com/datarecoverywizard/](http://www.easeus.com/datarecoverywizard/)

I used the software given in the above link.

It took nearly 13 hours for completing the recovery.

But i must say, all the recently added data was recovered. I couldn't recover my valuable pdfs and some tutorial videos...

I pray that no one must face such a scenario.

---

