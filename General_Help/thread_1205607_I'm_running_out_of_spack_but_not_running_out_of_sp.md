---
title: "I'm running out of spack but not running out of space???"
date: 2009-07-06
forum: General Help
---

### Post by 1oooop on 2009-07-06
today, I faced a confounding problem...

I ran out of space. ](*,) 

but when I looked to see what the problem was in Disk Usage Analyzer it showed me this...

[IMG]http://i169.photobucket.com/albums/u201/1oooop/Screenshot-DiskUsageAnalyzer.png[/IMG]

now... I'm already frustrated enough... when will this end!!!

by the way, I'm using ext3

---

### Post by ibutho on 2009-07-06
What is the output of running 
```
df -h
```
It seems like your / (root) partition is full.

---

### Post by 1oooop on 2009-07-06
[IMG]http://i169.photobucket.com/albums/u201/1oooop/Screenshot-brandonGravygod.png[/IMG]

---

### Post by Celauran on 2009-07-06
Yep, see how you've used 65GB out of 71? If this seems unusual, you can see where the disk space is being used with:

```
sudo du -sh /*
```

---

### Post by megamania on 2009-07-06
there's system-reserved space which you can get back.

I'm not at home now, but you can check tune2fs:
```

man tune2fs

```
and see if it helps.

---

### Post by drs305 on 2009-07-06
1oooop,

I wrote a guide about finding out what happened to all the free space - how to find lost space and how to recover it.

The three most common problems are not emptying the trash bin (user's and root's), large log files, and mistakenly copying data to the system partition instead of an external backup or other partition because the device wasn't mounted at the time (especially sbackup).  **ADDED: Your /var folder looks pretty large, which is where the log files are located.**

If it's the system partition, you can get a better idea of what is happening by unmounting all but the system partition, since mounted devices can hide the problem. Hint: If you unmount everything and still have a large amount of data in "/media", it probably isn't supposed to be there.

Take a look at the guide, which can walk you through the process of finding the problem. The link is "DiskSpace" in my signature line.

---

### Post by ugm6hr on 2009-07-06
> **megamania said:**
> there's system-reserved space which you can get back.

I think this is a deliberate setting to ensure you don't truly fill the HD.

If you do fill the HD, it can be impossible to recover the situation.

---

### Post by megamania on 2009-07-06
> **ugm6hr said:**
> I think this is a deliberate setting to ensure you don't truly fill the HD.

If you do fill the HD, it can be impossible to recover the situation.
It can actually be a problem if you completely fill up the root partition.

I have disabled the system-reserved space on the home partition for years now, with no problems at all.

Since it looks like the OP has a single partition, you are right and he should be careful. If he really needs some space, I'd advice to reduce the reserved space from 5% to 2% or 1% (in other words, NOT to completely disable it).

Anyway, **read the man page before doing anything!**

---

### Post by 1oooop on 2009-07-07
> **drs305 said:**
> 1oooop,

I wrote a guide about finding out what happened to all the free space - how to find lost space and how to recover it.

The three most common problems are not emptying the trash bin (user's and root's), large log files, and mistakenly copying data to the system partition instead of an external backup or other partition because the device wasn't mounted at the time (especially sbackup).  **ADDED: Your /var folder looks pretty large, which is where the log files are located.**

If it's the system partition, you can get a better idea of what is happening by unmounting all but the system partition, since mounted devices can hide the problem. Hint: If you unmount everything and still have a large amount of data in "/media", it probably isn't supposed to be there.

Take a look at the guide, which can walk you through the process of finding the problem. The link is "DiskSpace" in my signature line.

actually, the large var file is because of my webserver.

---

### Post by 1oooop on 2009-07-07
> **ibutho said:**
> What is the output of running 
```
df -h
```
It seems like your / (root) partition is full.

I it seems it is. The trash bin was the problem :P

---

