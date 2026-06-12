---
title: "Uninstalling Windows With A Wubi Install"
date: 2012-08-04
forum: General Help
---

### Post by Shie6meepo on 2012-08-04
Hello, everyone. I got a new computer two weeks ago (my old HP Mini went wrong in so many ways at the exact same moment that is just wasn't worth trying to fix), and of course I immediately put Ubuntu on it. However, I used the Windows installer for Ubuntu because it seemed convenient when I saw it on the page. I did not realize at the time that what that service really did was install Ubuntu completely inside of Windows.

Since that point I've uploaded about 50 CDs, configured many of my favorite programs in ways that I don't want to go through again (I'm a relative novice when it comes to commands and code, so editing program files was really fun), and done an install of many different shells that I like to switch off between. I was happy with my setup, and ready to be rid of Windows.

Then I realized through a bit of looking at the OS-Uninstaller thread that I can't exactly do that. I have no external hard drive and due to a recent move I have no friends to borrow one from, and I do not want to start from scratch again and spend two weeks getting everything back together the way I have it now.

So it all comes down to these questions: Is there a way to separate a wubi install from Windows without losing files, and to uninstall Windows from my machine while retaining Ubuntu, all of my modified versions (I have Lubuntu, Xubuntu, and a straight-up Openbox shell or lack thereof), and all of my files and preferences? In addition, is any possible route easy enough that I, without any mentionable experience with code, could attempt it without losing everything?

Thank you for your help and I await your replies with anticipation.

---

### Post by lisati on 2012-08-04
You'll need to backup or move your important data before removing Windows, otherwise things will disappear.

Have a look here: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by Shie6meepo on 2012-08-04
> **lisati said:**
> You'll need to backup or move your important data before removing Windows, otherwise things will disappear.

Have a look here: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
So, do all the files get deleted or simply lost in the migration, or is the migration process just flimsy enough that things fall out?

Thanks for the reply.

---

### Post by LiamOS on 2012-08-04
EDIT: I'm pretty sure the above example simply migrates your system, so it would be largely identical. You would have to create a new partition for it first, for which I'd recommend gparted if you're new to it(You'll need a blank CD).

Or my crazy way...
If you're completely unable to procure some external storage, there is a way to do it, but it could be quite advanced, depending on how comfortable you are with linux. This will also not really work for program configurations unless you copy the files over manually, which you may be able to do for some.

You could download and burn a copy of gparted and use that to shrink the partition on which windows resides. With the free space(However much you need), create a new partition in something like ext4(Remember what size it is). In Ubuntu, the partition should be detected when you start it again, so you can create a folder on it (call it anything other than your username), and move your files to it. 
At this point, you can boot up an installation CD and go to install. When you get to partitioning, choose advanced. Wipe the Windows partition(Assuming you want to), and partition the space however you want.
[ If you're not particularly fussed, do three partitions; /boot (~500m), swap (~twice your RAM) and / (rest of the free space) ].
Make sure you completely ignore the partition you created for your files, and that you don't format it. 
Now you can boot into Ubuntu, so when you do, copy your files from the partition onto your new Ubuntu installation. Now that you have your working Ubuntu installation with your bits and pieces on it, you can boot up gparted again, wipe the spare partition and expand / to fill it.


That's a fairly convoluted way about it, but it may be the only way.
Best of luck with whatever you do!

---

### Post by Ubun2to on 2012-08-04
> **ssrock64 said:**
> So, do all the files get deleted or simply lost in the migration, or is the migration process just flimsy enough that things fall out?

Thanks for the reply.

I migrated from Wubi, and I can successfully say that it is possible to migrate without losing any data.
One thing I messed up on to begin with-I never mounted my drive, and it took me awhile to figure out where the Wubi virtual disk was.

---

