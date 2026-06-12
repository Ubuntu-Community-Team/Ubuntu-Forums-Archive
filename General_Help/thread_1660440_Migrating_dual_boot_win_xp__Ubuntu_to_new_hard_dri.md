---
title: "Migrating dual boot win xp / Ubuntu to new hard drive"
date: 2011-01-05
forum: General Help
---

### Post by Mahler122 on 2011-01-05
I'd like to take my 250GB dual boot hard drive and migrate it onto a new 500GB hard drive. I have 1 partition(ntfs) for windows, 1 partition(ext4?) for ubuntu, 1 partition(swap) for swap, and 1 partitiion(ntfs) for data (Games).
I have GRUB on this drive, and everything works great currently.
The drive is getting quite old and I'd like to move everything plus an expansion for my Games partition.
Would simply creating appropriate partitions, and copying them to the new drive while running on the old drive do the trick? i.e. would the boot sector stay the same? Or is there some special procedure that I should follow to make this work?

Thanks in advance for any help with this matter

---

### Post by cariboo on 2011-01-05
Give [Clonezilla]("http://clonezilla.org/") a try, I use it all the time for cloning hard drives.

---

### Post by seawolf167 on 2011-01-05
> **cariboo907 said:**
> Give [Clonezilla]("http://clonezilla.org/") a try, I use it all the time for cloning hard drives.

+1 for Clonezilla, you can move individual partitions or the entire drive (and also do drive-to-drive so you don't need a hdd to store the images in the meantime)

---

### Post by Mahler122 on 2011-01-06
> **cariboo907 said:**
> Give [Clonezilla]("http://clonezilla.org/") a try, I use it all the time for cloning hard drives.

This seems to have worked for the most part. I have run into a bit of a problem though.. I moved some partitions around and deleted an unecessary partition on the cloned drive. Then I tried starting again. ubuntu works fine. However windows gets to the second splash screen (the one after the black splash screen with a progress bar. i.e. it's blue with a windows xp logo in the center), and it just sits there. I'm not sure why it's doing this, but probably this isn't the best place to ask since it's an ubuntu forum.

---

### Post by oldfred on 2011-01-06
It may be related to this:

Herman on windows disk identifier in MBR post #8:
[http://ubuntuforums.org/showthread.php?t=1378527](http://ubuntuforums.org/showthread.php?t=1378527)

Or if partition start & end are not identical you may have to update NTFS partition boot sector. Windows repairs all can be done from the XP disk, but most can be done from Ubuntu except chkdsk.

---

### Post by Mahler122 on 2011-01-10
Thanks for the suggestion of Clonezilla. This ended up working. I tried cloning the drive again, but this time i didn't delete the unnecessary partition. Windows booted up like it usually did after a disk check.

As far as the splash screen is concerned, I'm not sure why not removing the unnecessary partition fixed this, but it might be related to drive letter assignments or something.

I had to do some additional fixing with windows, but those problems existed before I transfered to the new hard drive. I've fixed these and my computer is back to it's original glory with a larger OS hard drive.

---

