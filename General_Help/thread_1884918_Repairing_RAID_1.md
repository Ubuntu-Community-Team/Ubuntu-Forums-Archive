---
title: "Repairing RAID 1"
date: 2011-11-22
forum: General Help
---

### Post by jonnny_j22 on 2011-11-22
High all, my desktop (dell e520) up until yesterday was running it's two 160gb hdds in a raid 1 array to ensure the OS's were safe - and good thing too!

After the bios, the boot process displays the RAID status of the motherboard's raid controller - and for the first time ever it said

Status: Degraded, Bootable: Yes

SATA 0: long-old-hdd-number status: Error Ocurred
SATA 1: long-old-hdd-number status: Normal

windows and ubuntu start fine, booting off SATA 2, but I've noticed now that the raid has degraded, sata1 now appears in Nautilus in Ubuntu and Computer in Windows 7.

As I can read/ write to the other drive, I'm suspecting that it's still working and the error is something got written to one but not the other, but I can test that later.

What I'm concerned with is restoring the RAID array - Is it a case of put the drive from SATA 1 in SATA 0, a blank drive in SATA 1, and then creating a RAID 1 for them? will this copy all data to the blank disk, or erase the mbr of both?

I gues what I'm asking is how do I add a blank drive to a degraded array? does the location (SATA 0/ SATA 1) matter?

Many thanks!

---

