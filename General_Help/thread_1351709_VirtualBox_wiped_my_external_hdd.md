---
title: "VirtualBox wiped my external hdd"
date: 2009-12-10
forum: General Help
---

### Post by notkaj on 2009-12-10
So I was running Windows XP as a guest OS in Ubuntu (9.10) and I tried mounting my external hdd (SATA -> USB, FAT32) to the guest OS through VirtualBox's USB support. When the guest OS finally recognised the HDD it complained about it having a RAW filesystem and asked if I would like to format it. I of course said no thanks and unmounted immediately.

Later, when I checked to see if the HDD was still OK I found that all of the directories were still in tact, but almost all of my files had vanished. When I right click on the drive and select properties, the used space/ free space is exactly as it was before, but when I open the drive, select all the folders, right click and select properties, the used space isn't even close to where it was before.

I'm pretty sure the data is still there, I just need a way of getting the files back. TestDisk doens't recognise the files as deleted, so file recovery doesn't sound like much of an option. I hope there's an easy way to fix this so that I don't have to take my hdd to some sort of specialist.

---

### Post by cholericfun on 2009-12-10
sounds familiar (but without the VMBox)
eventually gparted found the partition and fixed the errors on it in 3 seconds. 

(check -option)

theres other ways i guess but this must be the easiest (click and enter)

---

