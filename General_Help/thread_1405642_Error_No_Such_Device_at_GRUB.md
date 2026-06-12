---
title: "Error: No Such Device at GRUB"
date: 2010-02-12
forum: General Help
---

### Post by Xora on 2010-02-12
Hello, so heres the issue, and thanks beforehand. I am running a Windows 7/Karmic Koala Dualie. I was running Windows 7 first, Shrank Windows, partitioned the drive using the 40 free unallocated gigs of the 300 gig hard drive, and installed a fresh install of Karmic Koala to that. This has been working just fine (minus a few graphic driver issues) for the last week or so. Then wanting all my content to be available to both system and my network easily I decided to shrink the Windows 7 side, and use the 90 now free gigs to create a FAT32 Partition (using Partition Wizard after I had defragged the disk) The process runs fine, I boot back into Ubuntu where I have made my Windows 7 drive NTFS partition mount automatically, and I pull my videos and music to the new partition. At this point everything is going great till I fill the partition, and I decide to boot back into Windows to decide if I need to shrink windows to make the new partition any bigger. Well this time I go to GRUB hit windows and I get:
Error: No Such Device: 01caab4e3c9fb9e0

Wow, that was unpleasant. My roommates need the Windows 7 side, so I need to try fix this soon.

---

### Post by Xora on 2010-02-12
I would like to add windows 7 is still accessible from ubuntu

---

### Post by byStanderone on 2010-02-12
...assuming that you can still boot your karmic, have you tried sudo update-grub? if u've done this, have you also tried re-installing grub from your live cd?

---

### Post by Xora on 2010-02-12
Yes I could boot in Karmic, and yes sudo update-grub did the trick. Thank you so much!

---

