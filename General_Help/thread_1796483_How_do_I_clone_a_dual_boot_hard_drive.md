---
title: "How do I clone a dual boot hard drive"
date: 2011-07-03
forum: General Help
---

### Post by donofrij on 2011-07-03
I currently have a 160GB hhd running Ubuntu 11.04 and Windows XP, with the following partition configuration:

sda1 Windows NTFS (primary-active and boot and system)
sda5 Linux Swap (logical)
sda6 Linux Ubuntu ext3 (root)
sda7 Linux Ubuntu ext3 (home)
sda2 other

I have Grub2 installed, which provides me the choice at boot to start either Ubuntu or XP. This currently works fine.

I want to clone this hhd and transfer to a new, larger hhd, and have several questions, since I don't want to make a mistake with something so crtical.

1) Which software is generally considered the safest, most reliable and easiest to use (dd, Gddrescue, Clonezilla, Paragon, Macrum Reflect, Easeus, Drive Image XML, or something else)?

2) Which software will be able to copy and include _both_ operating systems in the partitions to be cloned?

3) Will that software change the booting process or options in the cloned copy in any way? I've read where using Easeus corrupts Grub2 and thus requires re-installing Grub2! 

Are there any other concerns, considerations or factors I need to consider in cloning the hhd; e.g. prior formatting an external hhd, and with what file system?  I've also read where FAT32 would be the choice, but don't really know for sure.

Thanks.

---

### Post by wildmanne39 on 2011-07-03
> **donofrij said:**
> I currently have a 160GB hhd running Ubuntu 11.04 and Windows XP, with the following partition configuration:

sda1 Windows NTFS (primary-active and boot and system)
sda5 Linux Swap (logical)
sda6 Linux Ubuntu ext3 (root)
sda7 Linux Ubuntu ext3 (home)
sda2 other

I have Grub2 installed, which provides me the choice at boot to start either Ubuntu or XP. This currently works fine.

I want to clone this hhd and transfer to a new, larger hhd, and have several questions, since I don't want to make a mistake with something so crtical.

1) Which software is generally considered the safest, most reliable and easiest to use (dd, Gddrescue, Clonezilla, Paragon, Macrum Reflect, Easeus, Drive Image XML, or something else)?

2) Which software will be able to copy and include _both_ operating systems in the partitions to be cloned?

3) Will that software change the booting process or options in the cloned copy in any way? I've read where using Easeus corrupts Grub2 and thus requires re-installing Grub2! 

Are there any other concerns, considerations or factors I need to consider in cloning the hhd; e.g. prior formatting an external hhd, and with what file system?  I've also read where FAT32 would be the choice, but don't really know for sure.

Thanks.Hi, a lot of people use clonezilla and say it works very well.
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by donofrij on 2011-07-04
Thanks. Actual historical experience is the best testamony. I'll give it a try.

---

### Post by scott092707 on 2011-07-13
Hi.  I have a similar situation:  I also dual-boot Windows (XP) and Ubuntu.
I cloned an old hard drive to a new, after removing them from a computer that became defunct as I was attempting to get it to recognize both drives for the copy.

I originally was planning to copy my old hard drive onto a new one and use that, as the old one is as old as the computer was (2002), and I was worried how long it would last.
First, I could not get the computer to recognize both the old drive AND the new.  It was one OR the other.  Finally, it did recognized NEITHER drive, NOR the cd/dvd drives.  I was advised that the IDE controller was probably at least flakey, if not shot, and as that was on the motherboard, that was basically it for my old computer.
I went to a computer place and had them assemble a new computer, sans hard drive (as I had two already), and sans OS (as I had a dual-boot Windows/Ubuntu).  I found a motherboard that had both IDE and SATA controllers (new drive was SATA, with SATA->IDE adapter).

I then used an Ubuntu Live-CD to  "dd"  the old drive to the new.  OK, although the progress reports (using the kill/watch commands found here or elsewhere), seemed to indicate that most of the time, the Records Out were one less than the Records In.  "diff"  was singularly unhelpful, as after an hour or so it told me that the "files" (/dev/sda , /dev/sdb) differed. Period.  I assumed that it would tell me individual files that differed, so that I could deal with them individually.  No.
I took a chance and booted from the new drive.
Linux: no problems.  At all.  (New computer is nice and speedy, too.)
Windows: "Huh?!?!"    Either Windows (XP, SPIII?) is way less adaptable to being placed in a new environment than Linux, or perhaps the differing sections of the drives happened to coincide with really important parts of Windows, as it will not boot Windows.  The first time, it just re-booted.  Then, it put up a "Could not successfully boot Windows the last time." message and gave me several options, all of which lead, sooner or a bit later, to another reboot.

If any other dual-booters who have had to migrate to a new system have any ideas how to bring back Windows (for the few things we need it for (like MagicJack, and sites that don't work with GNash), PLEASE give me some hints.

ALSO:

I used   "e2fsck -fvC 0"   to check out the two Linux partitions (/, /home), and almost instantly (why so fast? - I thought fsck took some time to work...) received lots of info (but curiously, apparently no numeric return code...), buried within which was the fact that NO bad blocks were found.  It looks as if it will be safe to continue using Ubuntu (which seemed likely, as I have been able to repeatedly boot successfully).

Does anyone think that perhaps I should do the copy again, perhaps with a different program?  Gddrescue, perhaps...
(I have made minimal changes, thinking that a 2nd copy might turn out to be advisable.)

Would  "fsck"  be able to successfully examine or better yet repair the ntsc Windows partition? 
It is not, of course, guaranteed that copy errors are causing the Windows non-boot.  It may well be that the new environment is the issue.  IF I have the Windows disks that came with the computer in 2002, I suppose I COULD dig them out (45 minutes away, in a storage facility) and re-install.  But with close to 10 years of updates, it would take forever to install, I would think...

Ideas?

-Scott

---

### Post by frankgee57 on 2012-07-21
> **scott092707 said:**
> Hi.  I have a similar situation:  I also dual-boot Windows (XP) and Ubuntu.
I cloned an old hard drive to a new, after removing them from a computer that became defunct as I was attempting to get it to recognize both drives for the copy.

I originally was planning to copy my old hard drive onto a new one and use that, as the old one is as old as the computer was (2002), and I was worried how long it would last.
First, I could not get the computer to recognize both the old drive AND the new.  It was one OR the other.  Finally, it did recognized NEITHER drive, NOR the cd/dvd drives.  I was advised that the IDE controller was probably at least flakey, if not shot, and as that was on the motherboard, that was basically it for my old computer.
I went to a computer place and had them assemble a new computer, sans hard drive (as I had two already), and sans OS (as I had a dual-boot Windows/Ubuntu).  I found a motherboard that had both IDE and SATA controllers (new drive was SATA, with SATA->IDE adapter).

I then used an Ubuntu Live-CD to  "dd"  the old drive to the new.  OK, although the progress reports (using the kill/watch commands found here or elsewhere), seemed to indicate that most of the time, the Records Out were one less than the Records In.  "diff"  was singularly unhelpful, as after an hour or so it told me that the "files" (/dev/sda , /dev/sdb) differed. Period.  I assumed that it would tell me individual files that differed, so that I could deal with them individually.  No.
I took a chance and booted from the new drive.
Linux: no problems.  At all.  (New computer is nice and speedy, too.)
Windows: "Huh?!?!"    Either Windows (XP, SPIII?) is way less adaptable to being placed in a new environment than Linux, or perhaps the differing sections of the drives happened to coincide with really important parts of Windows, as it will not boot Windows.  The first time, it just re-booted.  Then, it put up a "Could not successfully boot Windows the last time." message and gave me several options, all of which lead, sooner or a bit later, to another reboot.

If any other dual-booters who have had to migrate to a new system have any ideas how to bring back Windows (for the few things we need it for (like MagicJack, and sites that don't work with GNash), PLEASE give me some hints.

ALSO:

I used   "e2fsck -fvC 0"   to check out the two Linux partitions (/, /home), and almost instantly (why so fast? - I thought fsck took some time to work...) received lots of info (but curiously, apparently no numeric return code...), buried within which was the fact that NO bad blocks were found.  It looks as if it will be safe to continue using Ubuntu (which seemed likely, as I have been able to repeatedly boot successfully).

Does anyone think that perhaps I should do the copy again, perhaps with a different program?  Gddrescue, perhaps...
(I have made minimal changes, thinking that a 2nd copy might turn out to be advisable.)

Would  "fsck"  be able to successfully examine or better yet repair the ntsc Windows partition? 
It is not, of course, guaranteed that copy errors are causing the Windows non-boot.  It may well be that the new environment is the issue.  IF I have the Windows disks that came with the computer in 2002, I suppose I COULD dig them out (45 minutes away, in a storage facility) and re-install.  But with close to 10 years of updates, it would take forever to install, I would think...

Ideas?

-Scott

I see that this thread has been idle at least a week, but figured I'd toss in my two cents...

I believe that your simplest route will be to re-install Windows. You didn't speak of any preparation made to Windows prior to moving it to the new machine. What leads me to believe this is the statement you made about Window's failure to boot, then re-boot; in the new machine. 

If you had only Windows on the drive, there are a few things we could try, but what complicates matters is that you have a dual-boot drive. The usual remedies to repair Windows don't work well.  I am assuming that Ubuntu is your "primary" OS, due to the comment you made about needing Windows only "for the few things... like MagicJack, and sites that don't work with GNash," and you would prefer not to put your Ubuntu install at risk.

Good luck!

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

