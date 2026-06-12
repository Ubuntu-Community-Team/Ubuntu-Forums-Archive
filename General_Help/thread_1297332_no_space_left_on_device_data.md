---
title: "no space left on device /data"
date: 2009-10-21
forum: General Help
---

### Post by kueifen on 2009-10-21
**I have a failed job with the ERROR msg:** 
**No space left on device /data.**
 
**The df -f indicates there are 13 TB space under /data:**
 
**12k-a:/data/production/dev4/run/excpr/us/20091014_1220 > df -h**
**Filesystem Size Used Avail Use% Mounted on**
**data 65T 53T 13T 82% /data**
 
**I also see from the df -i that inodes are depleted and none are **
**available within the file system to create any more files.**
 
**12k-a:/home/ma000004 > df -i**
 
**Filesystem Inodes IUsed IFree IUse% Mounted on**
**data 4194304 4194304 0 100% /data**
 
**I googled to find out how those inodes are generated and**
**how many should be needed to complete our cycle of production jobs.**
 
**Is there a formula available to help me diagnose/predict?**
 
**[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Will it be helpful to delete files in /data to free up inodes number under /data ? We tried to delete files that are not needed under /data ( around 8TB) , but we only see 2% ( df -i ) free of Inodes [/SIZE][/FONT][/SIZE][/FONT]**[FONT=Helv][SIZE=2]
**[SIZE=2][FONT=Helv]space .[/FONT][/SIZE]**
**[SIZE=2][FONT=Helv]12k-a:/home/ma000004 > df -i[/FONT][/SIZE]**
 
**[SIZE=2][FONT=Helv]Filesystem Inodes IUsed IFree IUse% Mounted on[/FONT][/SIZE]**
**[SIZE=2][FONT=Helv]data 4194304 4083136 111168 98% /data[/FONT][/SIZE]**
 
**[SIZE=2][FONT=Helv]LEHD12k-a:/home/ma000004 > df -h[/FONT][/SIZE]**
**[SIZE=2][FONT=Helv]Filesystem Size Used Avail Use% Mounted on[/FONT][/SIZE]**
**[SIZE=2][FONT=Helv]data 65T 44T 21T 68% /data[/FONT][/SIZE]**
 
**[SIZE=2][FONT=Helv]So let's say that we cleared at least 10% of the data that was on the disk (as well as at least 100,000 links), but we have reduced the inodes from 100% of capacity to only 98%. I cleared about 8terabyte in /data , and had a smaller percent impact on the number of free inodes. If we keep removing data, it's looking like we'll be gaining inode space at a much slower rate; and I don't think we have a good sense of how much inode space we will need for a complete production run.[/FONT][/SIZE]**
 
**[SIZE=2][FONT=Helv]So, does anyone has any theories about what is going on here? .[/FONT][/SIZE]**
**[SIZE=2][FONT=Helv]Your help is appreciate.[/FONT][/SIZE]**
 
**[SIZE=2][FONT=Helv]Thanks,[/FONT][/SIZE]**
[/SIZE][/FONT]

---

### Post by ibuclaw on 2009-10-21
Deleting large files won't help.
You have probably hit the limit because of the shear amount of tiny files you have.


One thing you can do is run **fdupes** on it.

```
sudo fdupes -r /data
```
That may take a while, but it will identify all duplicate files, including (most importantly) all the zeroed/empty files too.

edit:
Also, you have a maximum of 4.1 Million inode allocations across a 65TB drive, meaning that at setup time, you chose to have large inodes when you created the filesystem. Clearly this was a big mistake in your part.

edit2:
Also, 65TBs ... WoW ... :o

---

### Post by kueifen on 2009-10-21
So the solution is either run fdupes to clean up those zeroed/empty files or reduce the inodes size , am I right ?
 
I thought since the inodes reach the limit, increase the inodes size seems to be the direction ?
 
Please advise.
 
Thanks,

---

### Post by ibuclaw on 2009-10-22
> **kueifen said:**
> So the solution is either run fdupes to clean up those zeroed/empty files or reduce the inodes size , am I right ?
 
I thought since the inodes reach the limit, increase the inodes size seems to be the direction ?
 
Please advise.
 
Thanks,

The number of inodes should be a automated/calculated value at creation time. As it appears that you have hit your limit, you probably specified a certain large number for the bytes per inode - big mistake.

It is not possible to expand the number of inodes on a filesystem after it is created, so be careful deciding the correct value for this parameter.

If you wish to expand it, your only option is to backup all data on the drive, and reformat from scratch.

Regards
Iain

---

