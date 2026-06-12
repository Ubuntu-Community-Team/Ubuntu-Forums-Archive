---
title: "best fylesystem to store backups?"
date: 2010-03-17
forum: General Help
---

### Post by X1R1 on 2010-03-17
What will it be? I will use Clonezilla as the backup software, but I want to be able to see the backups from both Linux and windows. 

Is fat32 an option? I have very large files(game isos and stuff like that)

If fat32 isn't an option, what filesystem should I use?

I read [this]("http://ubuntuforums.org/showthread.php?t=577139") thread but it doesnt mention the software to use and I assume we wants only to be able to see it in Linux.

Regards and thanks in advance for the help

---

### Post by conradin on 2010-03-17
Despite the fact Microsoft uses NTFS and FAT filesystems, there are much better filesystems to save data to. Fat has huge security risks associated with it. NTFS, lacks journaling and back ups. 

ext3 & ext4 have journaling and multiple superblock and inode recovery options. 

NTFS will work with clonezilla, but wont offer you much support in the event your hard disk crashes. You could install linux inside windows on an NTFS system with wubi or something like that, or windows inside linux with virtualBox. Ethier of these options have performance drawbacks. 

your NTFS and Fat32 filesystems do not inherently support multi-filesystems where pretty much every linux filesystem does. The option is all yours.

---

### Post by akand074 on 2010-03-17
XFS is a very good file system for large files, XFS offers very fast throughput on large files and large filesystems. Very fast at formatting and mounting.Though its benchmarked a little lower than most for small files. ReiserFS is good for a large amount of small files. EXT4 is a good overall high performance. JFS is very stable. I doubt windows can see any of these though but these would all be much better than NTFS or FAT32. I heard there is software that allows windows to see these file systems. Don't know much about it though.

---

### Post by X1R1 on 2010-03-17
Great insights, learned a lot about filesystems, those recovery options you guys are talking about for ext3 are built in clonezilla?

---

### Post by endfx on 2010-03-17
I see 2 choices for you:

1) NTFS: All the Windows haters in here will bitch on moan about NTFS. Fact is NTFS is a very decent file system. It is used in  Windows Server 2003/2008 for very large database servers and file servers. Newer 2.6.X kernels support NTFS writing.

Contrary to what someone said above, NTFS does have journaling support.

2) EXT3: There are a couple of ways to access ext3 from windows. Check out:
[http://www.fs-driver.org/](http://www.fs-driver.org/) for one way. 
The following website also has a bunch of options: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows) 


Don't bother with fat32 if you're storing ISOs and such. fat32 has the 4GB file size limit and if you're storing ISOs you'll hit that limit sooner or later.

---

### Post by conradin on 2010-03-17
> **X1R1 said:**
> Great insights, learned a lot about filesystems, those recovery options you guys are talking about for ext3 are built in clonezilla?

CloneZilla is a program that backs up file systems it however is not in of itself a filesystem. 

The file sytems supported by Clonezilla are:
# Filesystem supported: ext2, ext3, ext4, reiserfs, xfs, jfs of GNU/Linux, FAT, NTFS of MS Windows, and HFS+ of Mac OS. Therefore you can clone GNU/Linux, MS windows and Intel-based Mac OS, no matter it's 32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used blocks in partition are saved and restored. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.
# LVM2 (LVM version 1 is not) under GNU/Linux is supported. 


prehaps youre looking for an alternate back up software?

---

### Post by X1R1 on 2010-03-17
> **endfx said:**
> 

2) EXT3: There are a couple of ways to access ext3 from windows. Check out:
[http://www.fs-driver.org/](http://www.fs-driver.org/) for one way. 



I have tried that software before and it didnt work because it needs the linux OS to be on a Primary and active partition, and I have a logical partition for ubuntu.

I will check out the other link though

---

### Post by X1R1 on 2010-03-17
> **conradin said:**
> CloneZilla is a program that backs up file systems it however is not in of itself a filesystem. 

perhaps you're looking for an alternate back up software?

I know clonezilla its just the software, what I meant its that if the recovery options for the ext3 filesystem can be accesed trough clonezilla...say the chkdsk or something like that

And regarding the alternate back up software, I also have Acronis True Image, but I dont like how it manages linux partitions (makes backup sector by sector), and I have a pretty big (1TB) hard drive so It would take forever to backup. Clonezilla is much faster.

---

