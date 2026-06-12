---
title: "General Formatting Help"
date: 2010-11-08
forum: General Help
---

### Post by MrJLBrown on 2010-11-08
I've had problems reinstalling Ubuntu--lots of crashes even in completely unmodified scenarios sans the provided updates. What I really want to do is just completely blank the drive to one one clean, unpartitioned lump. How do I go about doing this (I prefer to use Puppy Linux on my flash drive when I'm not in Ubuntu, so preferably a Puppy solution would be appreciated, but if not that's what live discs are for).

Additionally, if I have a completely unpartitioned hard drive, will Ubuntu create the proper partitions during the live install?

---

### Post by sgosnell on 2010-11-08
Boot from whatever external disk you like, liveCD or Puppy or whatever.  You just can't alter a drive you've booted from.  Run gparted and delete all the partitions, then add one which uses the entire drive.  You will need to give it the filesystem type, and any will do, because the Ubuntu installer will indeed repartition the drive if you tell it to, and format the partitions to whatever type you specify.

---

### Post by Quackers on 2010-11-09
Or just boot from the chosen live cd and install using the whole disk.

---

### Post by godspeedmav on 2010-11-09
If your system crashes alot, it might be dude to "partition errors, bad installations" and as/if you are willing to wipe the drive clean you could pop in your choice of Live CD/USB and follow this guide: [http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

if you have your installed ubuntu partition on /dev/sd1 or /dev/sd6 you could alter accordingly in the of=/dev/sda.

**_But please do note that whatever you do, do a backup of the things you want!_** :)

---

