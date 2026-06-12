---
title: "Unable to run linux programs on NTFS/FAT removable media"
date: 2012-05-18
forum: General Help
---

### Post by NekoMaster on 2012-05-18
Alright so I finally decided to give Xubuntu 12.04 a whirl, and I'm faced with the same problem I had before... I can't run linux programs from my flash drive, removable hard drives, or sd-cards.

Is there anyway to disable the security that prevents you from running linux programs on FAT32 or NTFS formated removable media? Or is there some way I can force Ubuntu/Xubuntu to run the programs?

BTW, I know you could mount these things, but that takes the fun out of "removable" because after you remove the media, it won't mount again. I want to get back to running my portable games in linux without having to copy and past things back and forth.

I miss how things where before 11.xx, I remember when I use to use only Xubuntu 10.04 on my desktop and laptop's (but I can't now since 10.04 doesnt support my netbooks intell wireless card), back then I could run what ever I wanted off my flash drive.

---

### Post by casebomber on 2012-07-14
I would love to know how this can be done as well...

---

### Post by mike555 on 2012-07-14
format the drives (or part of the drives) in gparted to EXT file system.

---

### Post by efflandt on 2012-07-15
For removable flash memory ext2 would probably work best.  A journaled file system like ext3 or ext4 would wear it more with more writes.

Just remember to unmount it first, which if it automounted you can do by opening the file manager and clicking on the little up arrow symbol to its right.

---

