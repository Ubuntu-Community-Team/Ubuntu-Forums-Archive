---
title: "unistalling ubuntu 12.04"
date: 2012-10-10
forum: General Help
---

### Post by samishal on 2012-10-10
OK so I installed Ubuntu 12.04 onto my desktop to see what it was like, but because of driver issues and a few other querks I decided to go back to windows bit of a shame but I need it for work. So I boot the Ubuntu live CD. Reformat the entire drive to NTFS and install windows 7. However I cannot boot knows as I get his : error:unknown file system
Grub rescue>

Would anybody be able to help as I've tried my Best at finding a solution but come up empty handed

Sam

---

### Post by critin on 2012-10-10
> **samishal said:**
> OK so I installed Ubuntu 12.04 onto my desktop to see what it was like, but because of driver issues and a few other querks I decided to go back to windows bit of a shame but I need it for work. So I boot the Ubuntu live CD. Reformat the entire drive to NTFS and install windows 7. However I cannot boot knows as I get his : **error:unknown file system**
Grub rescue>

Would anybody be able to help as I've tried my Best at finding a solution but come up empty handed

Sam

Clear disk, leave as unallocated/free space, Reinstall Windows & Let Windows do the formatting.

You obviously can't run windows repair if it won't boot.
There may be easier ways, but if windows doesn't recognize its own install, something went wrong.

If you have a large disk and think you want to install another OS sometime, this is a good time to size the windows partition.  Give it a certain amount by clearing the whole disk, create New partiton, sizing it, and finishing.  Don't format.  Windows will see the partition and install into it.  You may have to point it out though, to avoid taking the whole disk.

---

