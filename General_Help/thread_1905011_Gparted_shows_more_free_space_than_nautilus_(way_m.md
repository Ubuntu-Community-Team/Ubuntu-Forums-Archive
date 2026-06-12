---
title: "Gparted shows more free space than nautilus (way more)"
date: 2012-01-05
forum: General Help
---

### Post by Bramkaandorp on 2012-01-05
I don't know if this is the appropriate place but here goes:

When I look at my hard disks (external and internal) with gparted, it shows that I have more room than Nautilus tells me.

And it isn't what I would call logical either.

Gparted;

Disk 1

Size: 931,51
Used: 818,22
Free: 113,29

Disk 2

Size: 298,09
Used: 204,25
Free: 93,84

Good so far, if I take into account that it's an Ext3 formatting.

Nautilus:

Disk 1

Size: 916,9
Used: 850,2
Free: 66,7
Disk 2

Size: 293,4
Used: 214,5
Free: 78,9

Here's where the logics seem to end.

My google fu isn't as great as I hoped.

---

### Post by westie457 on 2012-01-05
Hi. have you emptied the trash at all? Another thing that might help is to force a file system check. This sometimes recovers space from left over deleted files.

---

### Post by Bramkaandorp on 2012-01-05
> **westie457 said:**
> Hi. have you emptied the trash at all? Another thing that might help is to force a file system check. This sometimes recovers space from left over deleted files.

I always remove the trash (and then the trash1000 folder), so yes. Good call though. The trash1000 folder was a problem in the past. Even though I emptied the trash bin, there would sometimes be residue in the trash folder.

As for the system check, that isn't as easy as it seems. I unmounted the disk, and then ran "fsck /media/ff6378b4-25f8-4beb-bd1c-02ed40e65ddf" (in root), but then it says that the directory doesn't exist (which is to be expected when it's unmounted).

It looks to be an infinite loop. The disk has to be unmounted to be checked, but it has to be mounted to be read.

ETA: I'm running a system check now via the disk tools (a real d'oh moment right there. I cleanly forgot about the program). Fingers crossed.

Another edit: The test didn't change anything, sadly.

Could it be something inherent in either Gparted or Nautilus show an incorrect size, and only one of the two is right?

If so, I hope it's nautilus that's wrong, obviously.

---

### Post by rsvancara on 2012-01-05
What you need is a tie breaker.  Take a look at what fdisk has to say.  

sudo fdisk -l

---

### Post by killermist on 2012-01-06
EXT3 typically reserves 5% of the partition's size for superuser/root only access (and indirectly to help with preventing fragmentation).  So if you're looking at the partitions with tools that see as the superuser sees, and then as the user sees, then the free space numbers can be significantly different.
It could also be that the tools are using different versions of "human readable" numbers.

In marketing numbers (like for a long time advertised on hard drives) 1Gb is only 1,000,000,000 bytes instead of 1024*1024*1024 bytes (as it should be).  This could explain the difference in actual size, fairly likely.

---

### Post by Bramkaandorp on 2012-01-06
> **killermist said:**
> EXT3 typically reserves 5% of the partition's size for superuser/root only access (and indirectly to help with preventing fragmentation).  So if you're looking at the partitions with tools that see as the superuser sees, and then as the user sees, then the free space numbers can be significantly different.
It could also be that the tools are using different versions of "human readable" numbers.

Both sound reasonable, but my money is on the first. Don't ask me why, but somehow that one makes more sense.

Then again, how would that account for the apparent discrepancy?

Here's the thing: Disk 1 in Gparted has 113,29 GB free, and in nautilus it has 66,7 GB free space, whilst Disk 2 has 93,84 GB free in Gparted, but 78,9 GB free in Nautilus.

So even though Disk 1 has more space free than disk 2 in Gparted, it has less space free than disk 2 in Nautilus.

> In marketing numbers (like for a long time advertised on hard drives) 1Gb is only 1,000,000,000 bytes instead of 1024*1024*1024 bytes (as it should be).  This could explain the difference in actual size, fairly likely.

Could be, but then the discrepancy is even stranger.

---

### Post by Bramkaandorp on 2012-01-06
> **rsvancara said:**
> What you need is a tie breaker.  Take a look at what fdisk has to say.  

sudo fdisk -l

It's in Dutch, but that wouldn't be a big problem, would it?

Disk 1

> Schijf /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x000ddf1f

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdh1               1      121601   976760001   83  Linux

Disk 2

> Schijf /dev/sdg: 320.1 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00066d4a

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdg1               1       38913   312568641   83  Linux

---

### Post by killermist on 2012-01-06
> **Bramkaandorp said:**
> Both sound reasonable, but my money is on the first. Don't ask me why, but somehow that one makes more sense.

Then again, how would that account for the apparent discrepancy?

Here's the thing: Disk 1 in Gparted has 113,29 GB free, and in nautilus it has 66,7 GB free space, whilst Disk 2 has 93,84 GB free in Gparted, but 78,9 GB free in Nautilus.

So even though Disk 1 has more space free than disk 2 in Gparted, it has less space free than disk 2 in Nautilus.

Well, I'll try a little math and see what happens.

Disc 1, 1Tb (roughly, 1000Gb)
931Gb usable after formatting (using 1024^3 bytes per real Gb) (as supplied by gparted in 1st post)
818Gb used (as supplied by gparted in first post)
46.5Gb (5%)reserved by ext3 for superuser/root (calculated as 5% of 931Gb)
113Gb actual free space (=931-818, agrees with gparted value in 1st post)
66.5Gb made available "free" to user(s) (=113-46.5, happens to agree with the number by Nautilus in the first post)

Disc 2, 320Gb (roughly)
298Gb usable after formatting (from gparted, first post)
~15Gb reserved (5%*298)
204Gb used (from gparted, first post)
94Gb actual free space (=298-204, agrees with gparted, first post)
79Gb free space presented to user (=94-15, fuzzy match on free space presented by Nautilus, first post)

Looks to all add up straight to me.

---

### Post by Bramkaandorp on 2012-01-06
> **killermist said:**
> Well, I'll try a little math and see what happens.

Disc 1, 1Tb (roughly, 1000Gb)
931Gb usable after formatting (using 1024^3 bytes per real Gb) (as supplied by gparted in 1st post)
818Gb used (as supplied by gparted in first post)
46.5Gb (5%)reserved by ext3 for superuser/root (calculated as 5% of 931Gb)
113Gb actual free space (=931-818, agrees with gparted value in 1st post)
66.5Gb made available "free" to user(s) (=113-46.5, happens to agree with the number by Nautilus in the first post)

Disc 2, 320Gb (roughly)
298Gb usable after formatting (from gparted, first post)
~15Gb reserved (5%*298)
204Gb used (from gparted, first post)
94Gb actual free space (=298-204, agrees with gparted, first post)
79Gb free space presented to user (=94-15, fuzzy match on free space presented by Nautilus, first post)

Looks to all add up straight to me.

Well, that settles it then. At least I now know what was happening.

Thanks.

---

