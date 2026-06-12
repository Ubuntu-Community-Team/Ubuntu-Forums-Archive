---
title: "Resizing Windows partition"
date: 2010-03-21
forum: General Help
---

### Post by OneHero on 2010-03-21
Recently I decided to give Ubuntu 10.04 a try and I didn't like it + some drivers were really buggy so I deleted the partition. Whoops, I can't boot. I covered the process of how I fixed it on my blog [here]("http://lastcode.net/blog/fixing-boot-grub-deletion/").

Anyhow, now I'd like to expand my windows partition as there's 175gb of unallocated space. The problem is gparted won't let me expand it (trying this via liveCD). I've tried mounting/unmounting it—no luck. Any suggestions are most certainly welcome.

---

### Post by dcstar on 2010-03-21
> **OneHero said:**
> Recently I decided to give Ubuntu 10.04 a try and I didn't like it + some drivers were really buggy so I deleted the partition. Whoops, I can't boot. I covered the process of how I fixed it on my blog [here]("http://lastcode.net/blog/fixing-boot-grub-deletion/").

Anyhow, now I'd like to expand my windows partition as there's 175gb of unallocated space. The problem is gparted won't let me expand it (trying this via liveCD). I've tried mounting/unmounting it—no luck. Any suggestions are most certainly welcome.

You install the **ntfsprogs** package.

---

### Post by OneHero on 2010-03-22
> **dcstar said:**
> You install the **ntfsprogs** package.

How can I get the package if I don't have an internet connection on the LiveCD? I do have a flash drive by the way.

---

### Post by Mark Phelps on 2010-03-22
I didn't catch which Windows version you are running.  If it's XP, using GParted will probably work out OK, but I would recommend the GPArted LiveCD version -- which you can get from distrowatch.com.

If it's Vista or Win7, do NOT use GParted; instead, boot into Vista/Win7 and use the Disk Management utility to resize your OS partition.  Using GParted runs the risk of corrupting your Vista/Win7 OS partition and rendering it unbootable.

---

### Post by OneHero on 2010-03-22
> **Mark Phelps said:**
> I didn't catch which Windows version you are running.  If it's XP, using GParted will probably work out OK, but I would recommend the GPArted LiveCD version -- which you can get from distrowatch.com.

If it's Vista or Win7, do NOT use GParted; instead, boot into Vista/Win7 and use the Disk Management utility to resize your OS partition.  Using GParted runs the risk of corrupting your Vista/Win7 OS partition and rendering it unbootable.

Sorry, I have Windows 7 Home Premium x64. It looks like Windows won't allow me to resize my partition, and I can't seem to move the partitions around so the unallocated space is on the right. I can get a screenshot once I'm at my computer.

---

### Post by soltanis on 2010-03-22
This is odd, because I remember in Windows Vista there was a disk resize utility that allows you to expand and even shrink your NTFS partition. Are you saying Windows 7 doesn't have that? It's not an obvious thing but it's definitely there.

EDIT:
Yeah it does, here
[http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/](http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/)

---

### Post by Mark Phelps on 2010-03-22
> **OneHero said:**
> Sorry, I have Windows 7 Home Premium x64. It looks like Windows won't allow me to resize my partition, and I can't seem to move the partitions around so the unallocated space is on the right. I can get a screenshot once I'm at my computer.

Win7, like Vista, can be stubborn about not letting you shrink it much.  See the link below for some hints that will help:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Also, before you do any shrinkage, use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later if you need to make boot loader repairs.

---

### Post by OneHero on 2010-03-22
> **Mark Phelps said:**
> Win7, like Vista, can be stubborn about not letting you shrink it much.  See the link below for some hints that will help:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Also, before you do any shrinkage, use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later if you need to make boot loader repairs.

Already have a repair CD, thanks though. Also I want to EXPAND it, shrinking it is allowed.

---

### Post by OneHero on 2010-03-22
Ok so apparently it's a 170gb Free Space but it's an extended partition!?! When I tell it to delete it says theres not enough space on the disk...

Oh and ignore ANDREW (E) it's just my flash drive.

Perhaps creating a new partition in that free space, formatting it as NTFS, and deleting it would allow me to expand Windows?

EDIT: I can't seem to create or delete a new partition, not enough space...

---

### Post by Mark Phelps on 2010-03-22
Have you tried simply deleting the Extended partition?  That should return the whole chuck to free space -- into which you could then expand your Win7 partition.

If Disk Management utility won't let you remove the Extended partition, download and burn a GParted LiveCD from distrowatch.com., boot from that, and use that to remove the Extended partition.  Then go back into Disk Management and see if it will let you extend the partition.

---

