---
title: "In order to change my partition size, I should keep my HDD mounted right?"
date: 2010-10-08
forum: General Help
---

### Post by PsychedelicWonders on 2010-10-08
It's been a long time since I've been on ubuntu so bear with me

But I have a bunch of unallocated space on my HDD that I want to add to the Ubuntu partition

Right now my HDD Is mounted because I'm purging/installing grub

Normally after grub was finished updating, I am supposed to unmount the HDD, but can I leave it mounted and then go into gparted to adjust the partition size?

---

### Post by Scunizi on 2010-10-08
Boot to the live cd again.. you can't change a partition without unmounting it.. However if you're only dealing with the free space on the drive then you can use the installed system to manipulate it.. if large enough you could even turn it into your new /home so the next time you need to install you won't loose your data.

---

