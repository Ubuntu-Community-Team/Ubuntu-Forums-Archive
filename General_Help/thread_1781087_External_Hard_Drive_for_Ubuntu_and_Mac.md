---
title: "External Hard Drive for Ubuntu and Mac"
date: 2011-06-12
forum: General Help
---

### Post by Pragu on 2011-06-12
Hello all, I have what should be a fairly simple question.
I've been using Linux for a year or so now, and my last Mac has finally died. I still have the my favourite movies and music backed up on a 500Gb external hard drive, and have used it in the past to transfer music to my Ubuntu machine. I can not, however, transfer files from my ubuntu box to the external hard drive. It says the system is "read only" and that I am not the owner. To the best of my knowledge, it is HFS+ formatted.
So my question is two-fold: Is there any way I can make ubuntu play nice with HFS+ so I can back up my Linux computer on the existing partition, and if not, what format should I re format the drive to so that I can use it now, and in the future where a new Mac is possible?

thanks!

---

### Post by Herman on 2011-06-13
I don't know anything about hfs or Macintosh computers, but I noticed there are some packages you can install called 'hfsplus', 'hfsprogs', 'hfsutils' and 'hffsutils-tcltk'. Maybe some or those will help you. Probably you can try searching for those in Ubuntu Software Center and if you can't find them try Synaptic Package Manager and/or enable more software sources.

---

### Post by wildmanne39 on 2011-06-13
> **Pragu said:**
> Hello all, I have what should be a fairly simple question.
I've been using Linux for a year or so now, and my last Mac has finally died. I still have the my favourite movies and music backed up on a 500Gb external hard drive, and have used it in the past to transfer music to my Ubuntu machine. I can not, however, transfer files from my ubuntu box to the external hard drive. It says the system is "read only" and that I am not the owner. To the best of my knowledge, it is HFS+ formatted.
So my question is two-fold: Is there any way I can make ubuntu play nice with HFS+ so I can back up my Linux computer on the existing partition, and if not, what format should I re format the drive to so that I can use it now, and in the future where a new Mac is possible?

thanks!
Hi, this should help.
HOWTO: [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by srs5694 on 2011-06-14
Wildmanne39's link should help with permissions issues; however, a more fundamental problem is that the disk probably uses HFS+ with a journal. Unfortunately, Linux's HFS+ driver doesn't support a journal, and so it permits mere read-only access by default. You can overcome this limitation by including the "force" mount option, but nobody seems to know how safe that is. (The official documentation describes it as a "use at your own risk" option, and discussions of it on the Internet seem few and far between.) I've done this once or twice with no ill effects, but I make no promises. If you want to try it in an emergency, do it like this:

```

sudo mount -o force /dev/sdc1 /mnt

```

Overall, though, your best option is to remove all the data from the drive, put a new filesystem on it, and then copy the data back. For Linux-only use, I recommend ext3fs. (Many will suggest ext4fs, which is newer; but it offers few advantages over ext3fs for your purposes, and since ext3fs is older, non-Linux support for it is better, which could be more important in the future.) If you think it's likely you'll be using the disk with Mac OS in the future, then FAT is the most compatible choice; but FAT is limited to 4 GiB files, which may be unacceptable if you're storing movies on the disk. In that case, HFS+ is best, but you should create an *unjournaled* HFS+. This is the default if you create the filesystem in Linux, but you've got to change a check mark if you do this in OS X's Disk Utility.

Incidentally, I think there's a way to remove a journal from an existing HFS+ volume. I don't recall what it is, though, and it probably requires access to OS X. You could try Googling for it. If you can use another OS X system for a few minutes, that might be simpler than backing up, creating a new filesystem, and restoring your data.

---

