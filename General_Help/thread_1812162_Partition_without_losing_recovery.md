---
title: "Partition without losing recovery?"
date: 2011-07-25
forum: General Help
---

### Post by BobbiLinn on 2011-07-25
Hi :)

This is my first post on Ubuntu, ive been testing/and dual booted then reverted back to windows this past year, and now have gone back to school for computer networking...so im SUPER interested, but need some help.

So - i want to install Ubuntu on my little Toshiba netbook that i drag everywhere with me, but im afraid to screw with it's partitions.  I dont want to spend $$$ to get a larger than 8GB flash drive to create a recovery from the HDD partition that is installed on their, and they dont come with the backup/recovery disks, so i want to either leave that partition alone (in case i need to switch it back to windows down the road to sell it), or whatever.

I know i could just download windows to my PC, transfer the files to a flash drive, and put it on that way, but the recovery comes complete with drivers, etc which makes it a smoother and faster process.  Oh, i cant make the recovery of windows b/c i need 7.xx GB of space, and my biggest flash drive is an 8GB which doesnt quite make it.

SOOOOO - IF i install Ubuntu, will that recovery partition DEFINITELY be left alone?  Or is there an easy way someone could suggest copying that partition without a 16GB drive?  OR is there any way to use an external hard drive to copy that recovery partition on to?

I have only installed ubuntu once, maybe twice, but didnt care about partitions and wiped everything as requested by the install.  (i reverted back because i couldnt navigate quickly installing and updating programs, but now have a windows laptop and want to be forced to learn linux on my netbook).

any help is MUCH appreciated!  I have an Ubuntu scratch that im dying to itch, but dont want to lose my windows recovery.

Bobbi :)

---

### Post by 2F4U on 2011-07-26
What about getting a second hdd and replacing the original hdd with that? You can keep the first hdd in a save place and are 100% certain that nothing gets screwed up.

---

### Post by Jidolini on 2011-07-26
Thats great i've switched to ubuntu and this thing is cool men it keeps me busy and exited.

---

### Post by Mark Phelps on 2011-07-26
A major concern I have with anyone switching over a netbook is that there is often no optical drive usability for recovery.  All the repair/recovery CDs in the world don't help if you have no way to use them.

One problem you might be facing is that the drive could already be partitioned into four primary partitions -- the maximum number allowed.  If your netbook is running Win7, open the Win7 Disk Management tool and look at the list of partitions.  If you already have four, you are faced with a lot of work to install Ubuntu.

Regarding the recovery partition, it nearly always contains a big image file (among others) and that can't be split into smaller files to be written to DVD.  So, if you want to save that, you will have to get a large enough USB stick.

Also, before you do anything to the netbook, you really need to back off your current install -- and once again, you'll need a USB stick for that.  Don't know where you live, but around here, 8GB USB sticks cost $10 USD.

Also, you can read up on unetbootin -- you will need to use that to create a bootable USB stick containing the Ubuntu image you want to install.

---

