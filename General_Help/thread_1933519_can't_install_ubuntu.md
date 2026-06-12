---
title: "can't install ubuntu"
date: 2012-02-29
forum: General Help
---

### Post by stookin on 2012-02-29
hi  this is a bit difficult but I have 2 internal harddrives

I want 1 HDD with windows
and 1 HDD with a partition on which I install Ubuntu and another partition which I want to use for storage

how do I do that?

what I tried: I made 2 partitions on the ubuntu HDD 50 gb for ubuntu (FAT) 200 gb for storage (NTFS)
then when I wanted to install ubuntu gave me an error "No root file system is defined"  After some checking around, I decided to format the whole disk.

I made 3 partitions:
a swap partition
a ubuntu partition
and a storage partition

I just started installing and almost instantly I got this error:_[]("http://i.imgur.com/kKNr1.png")_
I could not navigate away from it.
I clicked "go back" "continue" the little cross in the upper left corner nothing happened.  I could however press ctrl alt del and get into firefox on ubuntu but when I clicked install ubuntu it all came back up (the error never left).
Also a error came up in ubuntu that ubiquity (I believe) had stalled.
So I had to shutdown by holding the computer on/off button for 10 seconds.

After that I went back into windows to format the entire hdd.
I tried to delete the partitions first. But an error occured and I all of a sudden had 4 partitions :s dunno what happened, something must have gone wrong

then the device was not shown in device administration anymore.  I could however still see with speedfan what the temprature and state of the hdd was, and right now I am performing an extended test on the HDD. the short test and the in depth analysis showed no errors and everything was either very good or good.

what the f is going on.?

---

### Post by Tiganjero on 2012-02-29
Erm, first of all you can't install Ubuntu on a FAT partition you need to use an ext format, but that doesn't matter since it wouldn't let you install on any other format. Anyway, your problem is probably caused by not using the right mount point, which should be / since you want to install it in the root of the chosen partition. So when installing Ubuntu, be sure to use an ext format and / as the mount point. You also mentioned that you were using swap, for which you just need to select swap as the file system. I hope this solves all of your problems.

Cheers,
George

EDIT: By the way, when you get to the point where it asks about where you want to install, pick manual partitioning, which will then launch GParted, which is a lot easier, and much better for partitioning when installing Ubuntu.

---

### Post by stookin on 2012-02-29
> **Tiganjero said:**
> Erm, first of all you can't install Ubuntu on a FAT partition you need to use an ext format, but that doesn't matter since it wouldn't let you install on any other format. Anyway, your problem is probably caused by not using the right mount point, which should be / since you want to install it in the root of the chosen partition. So when installing Ubuntu, be sure to use an ext format and / as the mount point. You also mentioned that you were using swap, for which you just need to select swap as the file system. I hope this solves all of your problems.

Cheers,
George
Ah, thank you!

the initial error was indeed caused by not choosing / as the mount point. That was solved later.
However I still don't know what happened afterward :s
I thought everything was OK, but then I got that second error and now I can't find my HDD anymore :s

I will try again right after the extended HDD test is done by speedfan

---

### Post by grahammechanical on 2012-02-29
This is the cause of the second error

> After that I went back into windows to format the entire hdd.

Windows had now turned the whole hard disk into a Dynamic disk. Those four partitions are only pretend partitions. But it is enough to fill up the four primary partition limit.

Ubuntu cannot install on a dynamic disk

[http://en.wikipedia.org/wiki/Logical_Disk_Manager]("http://en.wikipedia.org/wiki/Logical_Disk_Manager")

If you look here:

[http://www.tuxgarage.com/2011/02/manual-advanced-partitioning-in-ubuntu.html]("http://www.tuxgarage.com/2011/02/manual-advanced-partitioning-in-ubuntu.html")

You will find this under the heading **Windows Dual-Boot**


> If you are going to dual-boot Ubuntu and Windows 7, make sure your drive is a Basic disk and not a Dynamic one as Dynamic disk is Microsoft proprietary thing. Linux doesn't support it and you may end up losing some or all of your data. If you find that your disk is a Dynamic disk, Windows 7 partitioning tool can convert it to Basic for you but make sure to have strong backups of everything important on your drive.

That hard disk of yours is now a dynamic disk.

Regards.

---

### Post by stookin on 2012-02-29
Guess Hwat!

I'm running Ubuntu just fine.

I made a partition of 40gb for ubuntu on a 250 gb disk
I also made a 10gb swap partition

that's it.
In theory I should have between 200 and 210 gb of free disk space, which I could turn into a partition so I can use it as a storage for both Windows and Ubuntu.

Can someone tell me how to do this or give me a link?
Also I want to format it in NTFS so I can drop files >4gb on there. Is it recommendable to have such a partition next to a ubuntu partition?

Thank you in Advance.
BTW: I LOVE Ububntu!
It's fast, reliable and it looks neat :)
Also it 'feels' to run more solid than windows XP.

But that's just how I experience it.
I'm happy :P:D

---

### Post by stookin on 2012-02-29
I have one more question:

When I boot, it says it can not find my harddrive.
There are 3 options:
Wait
Cancel
or press m (I think it was) for manual recovery.

after waiting 30 sec it boots normally.

how come? and how to fix this?

---

