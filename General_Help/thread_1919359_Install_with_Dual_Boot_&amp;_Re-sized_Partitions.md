---
title: "Install with Dual Boot &amp; Re-sized Partitions"
date: 2012-02-02
forum: General Help
---

### Post by ddjolley on 2012-02-02
I have done a dual boot install with re-sized partitions using the canned procedure many times before.  This time, however, I want to make sure that I preserve the ability to use the contents of the manufacturers emergency restore partitions to return the computer to its factory set condition.   The current partition partition table looks like this:

                                   Size                       Used
/dev/sda1      ntfs          1.572GB               0.524GB
/dev/sda2      ntfs      128.465GB             43.560GB
/dev/sda3      ntfs        10.020GB               9.424GB

I suspect that /dev/sda2 is either the current data alone or the current data + the Windows OS.  I'm not real sure what the other two partitions are.  What I would like to do is shrink /dev/sda2 down to about 60GB, leave the other two partitions as they are, and install Ubuntu in the remaining disk space which is about 190GB since the total drive capacity is about 250GB.  I want to preserve the content of all 3 existing partitions with only /dev/sda2 shrunk.

What's the easiest way I can get this done?

Thanks for any help.

             ... doug

---

### Post by Quackers on 2012-02-02
Which version of Windows?
If you have only 3 primary partitions ( sda1 is probably a partition with boot files in it, sda2 is your Windows OS and sda3 is probably your recovery partition) on your disc and you still have unallocated space available there is no need to shrink sda2. If you shrank sda2 it would create a second area of unallocated space. As the 2 unallocated spaces are not physically next to each other you can't make them into one partition (or an extended partition).

You can install Ubuntu in the unallocated space that you already have (using logical partitions (not primary)).

It is important that you don't already have 4 primary partitions. You may just want to check that first.

---

### Post by ddjolley on 2012-02-02
I'm so sorry about this; but, I made a mistake on the size of sda2.  Actually sda2 has all the remaining disk space (which probably makes much more sense).  So, I actually actually have no extra disk space.  I need to re-size sda2.  How should I proceed?  Thanks (and sorry again).

           .... doug

---

### Post by oldfred on 2012-02-04
If Vista or 7 use the Windows tools to shrink the Windows partition, but not to create any new partitions. If XP just use gparted to shrink the XP partition and create new partitions. Reboot Windows several times before installing Ubuntu as it will want to run chkdsk or make other internal repairs on the resize.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Windows/NTFS needs about 30% free space to work well, so be careful not to shrink too much.

---

### Post by ddjolley on 2012-02-07
OK.  I completed the shrink using the tools in Windows 7.  The result is that I now have about 98 GB of unallocated disk space which is somewhat less than half the total disk capacity.  

Now, here's the big question.  If I partition the unallocated disk space as you have described and install Ubuntu, will I be able to (if I should ever want to) expand back the Windows partition that I just shrunk and restore the machine to it's original factory configuration *INCLUDING* restoring the Windows boot loader?

Thanks.  I think that we are getting there.

          ... doug

---

### Post by ecopccare on 2012-02-07
It shouldn't be too hard to do.  There should be tools in the recovery partition to do just that.  you can also easily delete your linux partition :'( and expand the windows partition (if you have windows 7 or vista, xp is a little harder, but you can do it with gparted as stated earlier.  If you want to restore the mbr there are tools like mbrwizard that can do that, or there is probably some kind of "boot repair" option on your recovery partition that will do about the same.  If you can spare the partitions, I always like to have my home folder as a seperate partition, larger than everything else, and formated to ext2 or ext3, and then install ext2fsd in windows and point my docs, my music, my whatever to that partition as well, so that i can conserve disk space and make both os's share data nicely

---

### Post by Mark Phelps on 2012-02-07
> **ddjolley said:**
> Now, here's the big question.  If I partition the unallocated disk space as you have described and install Ubuntu, will I be able to (if I should ever want to) expand back the Windows partition that I just shrunk and restore the machine to it's original factory configuration *INCLUDING* restoring the Windows boot loader?

Any answer we provide you to this is REALLY nothing more than a guess.  Why? Because, system restores are done by OEM routines and they do not all work the same.

In some cases, they will just erase the drive partitions (except for the recovery), reformat the remainder of the drive and reinstall from the compressed image.

In other cases, they will attempt to rewrite the Win7 OS and boot partitions -- and in this case, if either partition is smaller than the original, the routine can get confused and either refuse to run or fail.

What you MIGHT have to do, is boot from a Linux CD and use a partitioning tool to remove BOTH the Linux and Win7 OS partitions.  Then, the OEM restore tool should work OK.

---

