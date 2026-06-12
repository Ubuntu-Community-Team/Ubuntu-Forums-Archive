---
title: "Computer won't boot after interuppted distro upgrade"
date: 2011-06-09
forum: General Help
---

### Post by Pithikos on 2011-06-09
[Here]("http://ubuntuforums.org/showthread.php?p=10920289") is my story.

My distribution upgrade got interrupted in a hard way and when I start the computer I get some errors:
```
kernel panic - not syncing: VFS: unable to mount root on block 0, 0
``` or sth like this and a few more errors. Can't look the exact message as I am writing from the liveCD. On Gparted the boot looks normal and it is said that it's mounted but there is no mount point. There are things on the hard drive that I MUST save  :sad:

---

### Post by Pithikos on 2011-06-09
Ok now I seemed to be able and backup everything. Is there a way to fix this without installing a fresh copy of Ubuntu?

---

### Post by sanderd17 on 2011-06-09
Installing a fresh copy of ubuntu would be the best. Remove everything from your current partition except /home, then move the files from you home one level up (moving is not a lot of work, this is simply updating a reference, don't copy-paste because that is a lot of work and you have a backup already).

Now you can shrink that partition with gparted, shrink it so you have about 10 to 15GB of empty space (depending on the number of programs you will install afterwards, Ubuntu strictly has enough with 5GB). 

And finally install Ubuntu, chose manual installation and use the shrunken partition as your /home and format the empty space as ext4 and use it as the root (/).

This will be the easiest method to get everything back (including settings, excluding programs).

---

