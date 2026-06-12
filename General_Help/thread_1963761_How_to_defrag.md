---
title: "How to defrag?"
date: 2012-04-22
forum: General Help
---

### Post by Hungry Man on 2012-04-22
I know. Linux just about never needs to be defraged. I'm asking about, for those fringe cases, how to go about checking fragmentation and subsequently defragmenting.

Thanks.

---

### Post by 3Miro on 2012-04-22
AFIK there are no tools for defragging under Linux. The point is not that Linux rarely needs it, it is just the fragmentation cannot get so bad as to need a program.

Couple of years ago I asked about this and the only thing that people told me involved archiving the entire partition in one place, then deleting everything, then returning the archived files back (which overwrites all files and fixed defragging issues).

---

### Post by thenixedreport on 2012-04-22
There's a thread on [linuxquestions.org]("http://www.linuxquestions.org/questions/linux-general-1/defrag-on-linux-331862/") about the subject you just brought up.  One person responded with a way to check fragmentation but also noted that fragmentation will not go very high.

> Hi,
do a "shutdown -F"
and it will tell you how much it is fragmented when the system reboots. It will be less than 5% unless the disk is full. The only file systems that seem to get fragmented are: ms-dos fat 16, fat32, ntfs. And vms. Since the person who wrote most of VMS is now working for Microsoft it probably has the some bugs. When I used to fix hard drives on DEC systems it was common to back the systems to tape, initialize the original drive, restore it all back again.

nigelc

Still, if you want to optimize EXT3 or EXT4 filesystems, [ this post from WebUpD8]("http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html") may be what you're looking for.

---

### Post by dniMretsaM on 2012-04-22
There are a few tools. None are really actively maintained/developed, that I can see. I found [this](http://ubuntuforums.org/showthread.php?t=169551) buried on the forums. There was also e2defrag, but that has pretty much disappeared (and it was incompatible with ext4). I read something about e4defrag, but can't find it. I also saw a program called mdefrag, but again, no ext4 support.

---

### Post by Paqman on 2012-04-22
It's possible for a Linux filesystem to get significantly fragmented if it's run too full for a long time. To get rid of the fragmentation after sorting out the space problem you could back up the partition, wipe it, then restore the backup.

---

### Post by Hungry Man on 2012-04-22
Thanks for all the info.

---

### Post by Ceiber Boy on 2012-04-22
This is going to be one of those awful "I though I read somewhere" statements.

I thought I read somewhere that the Linux file system stored data in such a way (continuously, unless forced otherwise by a full disk), that fragmentation was a non-issue! And that if it did occur it would self rectify once the cause of the fragmentation was resolved!

---

### Post by dcstar on 2012-04-23
> **Ceiber Boy said:**
> This is going to be one of those awful "I though I read somewhere" statements.

I thought I read somewhere that the Linux file system stored data in such a way (continuously, unless forced otherwise by a full disk), that fragmentation was a non-issue! And that if it did occur it would self rectify once the cause of the fragmentation was resolved!

There are a multitude of different "Linux file systems", so blanket statements about all of them are virtually worthless.

AFAIK EXTx filesystems are pretty resilient to any fragmentation issues as long as they do not fill up - certainly much better than ancient filesystems like NTFS or FAT.

---

### Post by CharlesA on 2012-04-23
> **dcstar said:**
> AFAIK EXTx filesystems are pretty resilient to any fragmentation issues as long as they do not fill up - certainly much better than ancient filesystems like NTFS or FAT.

Yep. They preallocate space for files IIRC, which leads to lower fragmentation.

---

### Post by Ceiber Boy on 2012-04-23
> **dcstar said:**
> There are a multitude of different "Linux file systems", so blanket statements about all of them are virtually worthless.



I took it as red that we were talking about default Ubuntu file systems!

Sorry for the confusion.

---

