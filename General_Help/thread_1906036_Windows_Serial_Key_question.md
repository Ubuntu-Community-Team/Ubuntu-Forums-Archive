---
title: "Windows Serial Key question"
date: 2012-01-08
forum: General Help
---

### Post by Condor Cluster on 2012-01-08
Just a theoretical question here:

If I get a new laptop which will most likely have Windows 7 preinstalled, and format/install Ubuntu on it, can I reinstall Windows 7 back onto it in the future using the serial key on the sticker usually on the bottom of the laptop?

Most likely preinstalls don't come with discs, so I would have to find someone with a Windows 7 retail disc, but would the key that the laptop came with let you install Win 7 again?

Hope thats not too confusing! lol

---

### Post by howefield on 2012-01-08
Your new laptop would almost certainly have a way of restoring the operating system, whether that be via physical disks, hidden restore partitions, or by creating CD/DVDs.

Once you determine how to carry out an operating system factory restore, you can decide how you install Ubuntu.

---

### Post by Basher101 on 2012-01-08
> **Condor Cluster said:**
> Just a theoretical question here:

If I get a new laptop which will most likely have Windows 7 preinstalled, and format/install Ubuntu on it, can I reinstall Windows 7 back onto it in the future using the serial key on the sticker usually on the bottom of the laptop?

Most likely preinstalls don't come with discs, so I would have to find someone with a Windows 7 retail disc, but would the key that the laptop came with let you install Win 7 again?

Hope thats not too confusing! lol

Yes. I do not like how they did not include a DVD...if you pay hundreds of $ to get a laptop, they could have AT LEAST given you a 1 $ DVD disc....

Also Howefield is right about the restore partition, i had one too. still they could have included a dvd..

---

### Post by Pilot6 on 2012-01-08
Yes, you can. I did it many times. Installed linux on a laptop, then installed preinstalled Windows into VirtualBox with the same serial. It looks quite legal. :-)

---

### Post by Condor Cluster on 2012-01-08
I guess if I do swap Ubuntu for Win 7, I have to make sure I don't wipe over the restore partition then (is it a ghost image or something then?)

---

### Post by coffeecat on 2012-01-08
Most, if not all, Windows laptops these days come with a manufacturer's utility for preparing a set of restore DVDs. Make sure you create a set before you do any partitioning work, and try to keep the recovery partitionas well. Then you are double-covered for restoring Windows if you need to.

---

### Post by Mark Phelps on 2012-01-08
IF you Restore the Win7 install, you'll have to reinstall everything that didn't come preinstalled.

Another approach would be to image off the Win7 install to an external drive (or USB stick).  You can do that using the FREE version of Macrium Reflect. Download and install it in Win7, image off the install, and then create the Linux Boot CD.

That way, should you decide to restore it later, it will only take a few minutes -- and you don't have to worry about the Recovery partition.

---

### Post by Pilot6 on 2012-01-08
> **Condor Cluster said:**
> I guess if I do swap Ubuntu for Win 7, I have to make sure I don't wipe over the restore partition then (is it a ghost image or something then?)

This is not a problem. You can install Windows 7 from any installation disk. After you enter your serial it will determine, which exactly version of Win 7 you have (Ultimate, Home, etc).

---

