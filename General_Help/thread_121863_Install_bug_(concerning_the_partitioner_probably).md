---
title: "Install bug (concerning the partitioner probably)"
date: 2006-01-26
forum: General Help
---

### Post by Kalli on 2006-01-26
It seems that if I want to manually edit the partition table in install the installation prgram can't create a user account.  Everything works fine except the user account is not create so you get stuck in a cycle of re-entering the password (whle creating it btw).  I've tried out many things and it works fine if I use the "guided partitioning."

Anyone had experience with this?

---

### Post by johnnymo87 on 2006-01-26
Do you have another install disc? You might just have a bad CD.

---

### Post by steve.horsley on 2006-01-26
I don't want to pick a fight, but its not as simple as that. I have installed Hoary and Breezy several times, I have always used custom partitioning, and it never failed to prompt me for the initial username/password. So I suspect that there may be something specific to your circumstances that is upsetting the installer. 

I can't think of any good advice to give you, but the problem you describe is not universal in Ubuntu.

Steve

---

### Post by dodgeman79 on 2006-01-26
i had a similar problem with install not letting me set up a user/password.  found out that since I was trying to set my /Home to FAT32 to share files with Windows.  the installer didn't have anough rights to the drive to do that.  so after several tries at FAT32 I went back and used Guided Partitioning and let it set the /Home to the defaulst ext3 and everything went fine and no problems.

---

### Post by Kalli on 2006-01-26
Maybe it's just when I'm trying to make a fat32 /home drive... then I'm not crazy...that's good :)  Thanks for that dodgeman.  Just out of curiosity, what did you end up using for sharing?  All my ideas are a bit of a bother to do...

---

### Post by steve.horsley on 2006-01-26
Aaaaarggggghhhh!

Never, never, **never** use vfat for your Linux system. It is unable to store the file permissions and ownership info that is vital for a working system. You can use vfat for sharing files between Linux and Windows, but don't try and keep any system folders on there, just mount it as an extra. Symlink it from your home folder for easy access if you like.

For the Linux system, I suggest ext3 or reiserFS.

---

### Post by dodgeman79 on 2006-01-27
Steve, how much room should I save for my /Home directory?  reason I was trying for vfat is that it's the rest of my partition and about 40GB in size.  so I was wanting the 40GB to serve as double duty.  but now I want to reclaim part of it for storage/file access between the two OS's.

---

