---
title: "Need help with partitioning"
date: 2010-11-16
forum: General Help
---

### Post by drabina on 2010-11-16
I am trying to install Ubuntu on a computer that will do a dual boot (Windows XP and Ubuntu). My drive is 1.5TB. I have installed WinXP first creating 20GB partition for it. Rest of the drive remained as an unpartitioned space.

Now, on top of that I am trying to install Ubuntu. I got as far as the screen that asks me to partition hard drive. What I would like to do is to create the following partitions:

/ - where the system will go (20GB)
/swap - well, swap (5GB)
/media - for my media files (rest of the HD ~1.4TB)

Unfortunately, I was unable to do so (or it is beyond my noob Linux skills). The only two partition types available were Primary and Logical. When I created two partitions:

/ 
/media

I got an error that warned me to go back and "rethink" my strategy (do not remember exact error). When I tried auto-partition free space, I got:

/
/swap

but / took the whole remaining 1.5TB of the drive.

How do I create the three partitions that I would like to have?

Thanks.

---

### Post by wojox on 2010-11-16
You should be able to create four primary partitions. Windows, /, /swap, and /media. 

If that doesn't work create a / primary and /swap and /media as logical. 

I wish I had a TB drive. :)

---

### Post by bryanl on 2010-11-16
you can have up to four primary partitions, if you need more than that, you'd have to have 3 primaries and a logical partition to hold the rest.

Your plan appears to be one for XP, one for Linux root, one for swap, and one for 'media' - OK on partition count but Ubuntu defines /media for system purposes like where to automount external drives. That would conflict with your using it for your media files.

what I suggest you do is to set up a root linux partition with about 16 GB and the remainder of the drive as a /home mount point. Use a swap file rather than a swap partition (see [Move to swapfile rather than swap partition](http://tcl.leipper.org/?p=992)) - you will get a complaint on install about the lack of a swap partition but the swapfile will take care of that issue.

after you get your system installed, create a /home/media directory, set its permissions as needed for how you plan to use it, populate it and have at it.

---

### Post by drabina on 2010-11-16
Thanks for all the replies. I have managed now to create the partitions I need. I guess the problem was with the name of the partition I was trying to create. Once I renamed the big partition to /Media installer accepted the setup and did not complain.

Thanks again.

---

