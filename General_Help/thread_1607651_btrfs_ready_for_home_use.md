---
title: "btrfs ready for home use?"
date: 2010-10-28
forum: General Help
---

### Post by trikster_x on 2010-10-28
Okay, so I found a couple articles about the new BTRFS for Ubuntu that became available on 10.10, and I was wondering if some people could clear some stuff up for me.  I am going to be upgrading my desktop box from 8.04 soon (I know,long time coming, but I had some hardware compatibility issues with recent releases that have been addressed on my end) I'm pretty new to a lot of these terms, so a detailed explanation would be awesome if you don't mind.

1 - Is this file system ready for the home user?

2 - Are there significant performance gains over ext4 and is it stable?  If not now, will it be in the future?

3 - When a new subvolume is created, does that act like a partition?  For instance, would a home folder in it's own subvolume act like home on a separate partition in the event of a reinstall or upgrade to the root filesystem?  If not, what would be the specific advantages to using a subvolume?

4 - When creating a snapshot, is it bit for bit or a compressed image?

5 - Does compressing the root filesystem save a significant amount of disc space?  

6 - Is there anything else that would be important to know about this filesystem?

If I have some things confused or misunderstood, it is because I am just starting to understand how some of the foundational stuff in my OS works, and these forums are always the best place to get info from people who have experience with it.  

Thanks for any information you can provide.

---

### Post by kerry_s on 2010-10-28
1. i think so
2. i think so
 
the rest i don't know.

---

### Post by wcoenen on 2010-10-28
> 1 - Is this file system ready for the home user?

From the **[btrfs documentation]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=blob;f=Documentation/filesystems/btrfs.txt;h=64087c34327fe0ba11e790e0a41224b8e7c1d30c;hb=HEAD")** in the sources of linux 2.6.36:

> Btrfs is under heavy development, and is not suitable for any uses other than benchmarking and review. The Btrfs disk format is not yet finalized.

> 2 - Are there significant performance gains over ext4 and is it stable? If not now, will it be in the future?

I doubt it.  BTRFS focuses on advanced features, fault tolerance, repair and easy administration. File systems which don't have all that stuff should be a bit faster. The **[phoronix benchmark]("http://www.phoronix.com/scan.php?page=article&item=btrfs_benchmarks&num=1")** seems to confirm this. Personally I think that modern file systems are so close to each other that the performance differences don't matter for a home user.

> When a new subvolume is created, does that act like a partition? For instance, would a home folder in it's own subvolume act like home on a separate partition in the event of a reinstall or upgrade to the root filesystem?

Yes.

> When creating a snapshot, is it bit for bit or a compressed image?

Neither. I don't know what your background is so won't go into the details. But from an end-user's point of view, you can think of it like this:

A file system is a tree of objects. The root folder references files and subfolders. Subfolders reference yet other files and folders, etcetera.

A snapshot is also such a tree, which overlaps with the tree of the original file system. Originally the overlap is 100%, so making a snapshot can be done in an instant and doesn't take any extra space. As you make changes to the file system, it will start to diverge from the snapshot. The overlap between the trees decreases! Keeping the snapshot means that you use some disk space to keep any original files as they are deleted or changed.

> Does compressing the root filesystem save a significant amount of disc space? 

Not sure, I can't find any reference. I would guess it saves about 30%.

---

### Post by trikster_x on 2010-10-29
@wcoenen:

Thanks for addressing my questions.  That was basically what I was looking for.  I had actually found a decent explanation of what a snapshot does on a wiki site, so I am completely clear on that.  It is also clear that, while there are some interesting features for the casual home user (I'm really interested in the subvolume bit), this fs has more server and business uses in mind, where there must be regular backups of large amounts of data. 

I think for now I am going to stick with ext4, at least until everything is considered stable for home use, since I don't want to run a fs hodgepodge on my dedicated Ubuntu machine.

---

### Post by wcoenen on 2010-11-01
> **trikster_x said:**
> @wcoenen:
It is also clear that, while there are some interesting features for the casual home user (I'm really interested in the subvolume bit), this fs has more server and business uses in mind, where there must be regular backups of large amounts of data. 


I think that the snapshot feature has great potential for home users. It will make it possible to provide system rollbacks ("revert to the system from yesterday, which still worked") and something like Time Machine on Mac OS X to recover user files.

Also, [BTRFS was chosen]("http://lists.meego.com/pipermail/meego-dev/2010-May/002133.html") as the file system for MeeGo, a mobile OS being developed by Nokia and Intel.

---

