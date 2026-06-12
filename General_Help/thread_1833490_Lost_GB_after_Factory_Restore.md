---
title: "Lost GB after Factory Restore"
date: 2011-08-26
forum: General Help
---

### Post by GraveHeartz on 2011-08-26
This happened a few years back, though my computer still suffers from this issue. Cutting a long story short, as short as I can, I lost my GB (*295gb of space before Ubuntu*) after a factory restore because I did not like Ubuntu as much as I thought I would. A lot of things I couldn't do with Ubuntu that I can with windows. (*Before the factory restore, which I kept Ubuntu for awhile*) I downloaded Ubuntu by restarting my computer and booting into my CD. I presume I added 147gb to the Ubuntu download by looking at the 147 GB File System in ubuntu. I'll get to that later.

Anyway, I downloaded from the CD and added 147 GBs to my download with Ubuntu 10.10 (*Using 11.04 now, but downloaded the normal way with only 30GB of space*). After Factory Restore, I booted into my defualt OS - being Windows 7 - and I now had 148 GB, 100 GB free to use. I tried everything I could think of, which isn't much considering I know nothing about a computer, which landed me know where. I eventually decided to download 11.04 recently. It appears as though (*having searched through the **147 GB Filesystem** files containing my pictures I had in the cursed Ubuntu 10.10*) it is the Ubuntu (*Filesystem)* I once had before I restored my computer. 

I might also add that restoring the computer was my only option, as my method (*rather retarded*) did not add the Ubuntu into the Programs area for me to UN-install as an application. So, the question is; **Can I get my lost GB's back?**

I'll be awaiting an answer, be it bad news or good. If there is a similar question, I am sorry I did not look. I prefer to not waste my whole day/days searching for a similar question.

---

### Post by decrepit on 2011-08-26
While you're waiting for a definitive answer, some useful info would probably be if you did a "wubi" install or a proper dual boot?

If it's a wubi I have no idea.

If a proper dual boot, you would have created separate linux partitions on the hard drive.
Windows can't read these and just ignores them. It's possible your system restore had the same problem, leaving the linux partitions unchanged.
If that's the case you just have to delete them and expand the windows partition back to the whole hard drive.

---

### Post by GraveHeartz on 2011-08-26
I did reboot and then entered the CD. From there I installed Ubuntu. If that is the proper dual booting you speak of, how do you delete/find the linux partitions? Sorry for asking this if it is obvious. I'm not exactly good with computers.

---

### Post by decrepit on 2011-08-27
Sorry I'm very fuzzy on a "wubi" install, from what you say I can't tell what you've done.

You could try booting a ubuntu live CD, open a terminal and do
fdisk-l

That should come up with all your partitions and how they're formated.

gparted can delete any linux partitions, then expand the windows partition to fill your hard drive. But make sure everything is backed up first.

---

### Post by dino99 on 2011-08-27
real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by 3rdalbum on 2011-08-27
> **decrepit said:**
> Sorry I'm very fuzzy on a "wubi" install, from what you say I can't tell what you've done.

You could try booting a ubuntu live CD, open a terminal and do
fdisk-l

That should come up with all your partitions and how they're formated.

gparted can delete any linux partitions, then expand the windows partition to fill your hard drive. But make sure everything is backed up first.

That's exactly the advice I would have suggested. +1.

Make sure everything important is backed up. Then double-check that it is. Repartitioning has a 1% failure rate.

---

### Post by lisati on 2011-08-27
> **GraveHeartz said:**
> I did reboot and then entered the CD. 
Sounds like a Wubi installation to me. For a dual-boot with Ubuntu in its own partition, it's usually the other way round: insert CD then reboot.

---

### Post by GraveHeartz on 2011-08-31
> **decrepit said:**
> While you're waiting for a definitive answer, some useful info would probably be if you did a "wubi" install or a proper dual boot?

If it's a wubi I have no idea.

If a proper dual boot, you would have created separate linux partitions on the hard drive.
Windows can't read these and just ignores them. It's possible your system restore had the same problem, leaving the linux partitions unchanged.
If that's the case you just have to delete them and expand the windows partition back to the whole hard drive.

Well, this person right here helped me solve my issue. It was in fact a  separate Linux Partition that held my missing space. Unfortunately at  first, I could not resize my main partition. That is when I found  EASEUS, which did allow me to do so. I was not able to resize my  partition to it's fullest (I still believe there might be a partition(s)  belonging to the old Ubuntu with my other space on it) but I did not  feel safe deleting all my partitions just to get my lost space back,  while having the possibility of having to rebuild because I deleted  something important. I have 279gbs in all back so that is good enough  for me. Thanks everyone. :D

Reason it is hard for me to find the  other Ubuntu partitions is because they have no names. The only two  Partitions I have left are the eMachines (main; C:) and the System  Reserved. The other two I have have no names, one of them has 13gbs and  the other no-name has 5.82gbs. Again, thanks everyone.

**lisati**, that's what I meant. Sorry for that.

---

### Post by decrepit on 2011-08-31
Glad I've helped and you've improved things.
But the partitions don't really need names, you can tell by their format. 
Ubuntu will be either "ext3" or "ext4", windows will be "ntfs". I'm not sure about "system reserved", but it won't be "ext3" or "ext4".
I don't know anything about EASEUS, maybe it also doesn't recognise linux formats.
If you want to go further, most linux live Cds have "gparted" on them. That will give you the full story.

---

