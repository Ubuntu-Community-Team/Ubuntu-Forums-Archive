---
title: "Giving folder access on 2nd HDD to another local user"
date: 2011-02-26
forum: General Help
---

### Post by mindfire6482 on 2011-02-26
Hello, i was wondering of someone would be able to assist me in configuring my system (and helping me learn a bit in the process as i really am a complete newbie to Linux and have no clue how to administer it properly).

My Machine is used by myself for slightly geekier pursuits like web dev and audio production while my wife uses it for the usual stuff like facebook and games etc..

What i am trying to do essentially is this; I have a 2nd hard drive which contains some of my development and audio files but also contains her folder with MP3's and photo's etc.. So what i would like is a profile which she can log into with a her own background, colour scheme and the like but with access to ONLY her folder on the 2nd HDD, BUT here is the problem, Not only do i not know how to accomplish this but i cant even figure out how to give her access to the 2nd HDD as no matter what i try i cant seem to give her access to anything but the CD-ROM drive... could someone please advise me how to do this, I could do it in Windows but since my machine is a Ubuntu 10.10 machine only now im kind of flying blind..

Kind Regards
MindFire

---

### Post by ajgreeny on 2011-02-26
How is this second hard disk formatted, a fat or ntfs filesystem, or a linux ext# filesystem?  This will affect the way permissions are possibly set for the disk and folders.  If it is in a windows format, you will only be able to set permissions of the mount point, with an edit of /etc/fstab, but if it is in ext# format, you can allow different users different access permissions to separate folders.

Tell us more about the disk type (internal, external), and how it is attached and mounted, and a better answer may be possible.

---

