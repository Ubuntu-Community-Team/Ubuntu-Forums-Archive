---
title: "Windows 7 &amp; Ubuntu 11.10 - Add 5th Partition"
date: 2011-11-11
forum: General Help
---

### Post by Habboblob on 2011-11-11
Hi there guys.
I just recently updated my Ubuntu to 11.10 on MY DESKTOP PC. 1TB HDD.
It has 2 partitions, an extended, 74GB, and a SWAP which is 16GB.

I also created a further 2 partitions which has Windows 7 installed.
Windows 7 Parition - 90GB, Some system partition - 100MB.

I am trying to create a 5th NTFS partition where I could store my data, but gParted is telling me that I can only have 4 partitions. I read that you can only have 4 partitions, then why is this so?

My LAPTOP has Windows 7, Windows XP, Backtrack 5, and a NTFS data partition.
Here's a screenshot:
[IMG]http://i41.tinypic.com/33cyzit.png[/IMG]

Also, when I turn on my Laptop it has a grub screen which lets me choose BackTrack (Ubuntu 10.04) or Windows.
If I select Windows, it then loads the Windows MBR, which lets me pick Windows 7 or XP.

I basically want to be able to have the same on my DESKTOP as it was with my Laptop, but DO NOT need Windows XP.

Thanks :popcorn:

---

### Post by Mark Phelps on 2011-11-11
If you FORCE the creation of another partition, MS Windows will convert your Basic Volumes into Dynamic Disks -- something you do NOT want to do.

Don't know how you're getting away with more than 4 Primary partitions, but you really need to have a bunch of Logical partitions inside a single Extended partition.

If you want to do this inside of Windows, my suggestion is to download the ISO for Partition Wizard, burn that to CD, boot from that -- and use that to make the partition changes.

It also includes a function to convert Dynamic Drives to Basic Volumes.

---

### Post by Habboblob on 2011-11-11
> **Mark Phelps said:**
> If you FORCE the creation of another partition, MS Windows will convert your Basic Volumes into Dynamic Disks -- something you do NOT want to do.

Don't know how you're getting away with more than 4 Primary partitions, but you really need to have a bunch of Logical partitions inside a single Extended partition.

If you want to do this inside of Windows, my suggestion is to download the ISO for Partition Wizard, burn that to CD, boot from that -- and use that to make the partition changes.

It also includes a function to convert Dynamic Drives to Basic Volumes.

I was thinking about maybe re-installing Ubuntu 11.10, and then seeing if I could create another Partition.
;)

---

