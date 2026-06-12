---
title: "Hard drives (RAID1 via Firewire) setup help sought"
date: 2010-08-14
forum: General Help
---

### Post by fast_ian on 2010-08-14
Hi,

I searched, and unfortunately all that did was raise my confusion level on this..... "Grub"? "mdadm"? "fake"?, S/Wraid? Disk utility?.... etc.... So many options, so little understanding! :confused:

Relevant stuff (Mostly reported by "Disk utility"):
- Lucid Lynx.
- PATA host adaptor -> IDE controller -> Maxtor 164GB H/D [I *think* this has Windoze on it, but can't remember!] There's also a CD & DVD drive on this IDE bus.
- PATA host adaptor -> SATA controller -> Seagate 500GB H.D. - The Ubuntu boot drive, currently a 250GB ext4 partition, 3GB swap and 250GB "unused".
- Peripiheral devices -> Firewire 400 -> 2 x Samsung 500GB H/D's. These were "stolen" from my Mac Book and are currently a RAID1 Apple array. Everything they contained is safely backed up, and these can be considered as "new" drives awaiting formatting. [It's actually a Buffalo Drivestation Duo, but their site was even more confusing than here.  :eek: ]

Anyway, everything is working wonderfully, but I'd like to use the 2 F/W drives in a RAID1 array - So, eventually to the question: How do I tell Ubuntu to use these drives as a RAID array? It seems I can format and partition etc from disk utility. Do I then use mdadm for configuration? Any other recommendations?

TIA, cheers,
Ian

---

### Post by fast_ian on 2010-08-14
> **fast_ian said:**
> ....How do I tell Ubuntu to use these drives as a RAID array? It seems I can format and partition etc from disk utility.

Given the # of views, I figure I may as well "document" progress on this here - Maybe help someone else.

I have now formatted the 2nd Seagate drive in the Buffalo - 500GB, single partition, GUID partition table, currently unallocated. There are a *lot* of choices for file system, I went with good 'ol ext4, which was probably mistake #1...... There's a "Linux RAID" option, but I've got to investigate what that does (?)

FWIW, I ran the benchmark in disk utility on the drives before starting (only avg. read and access times reported):

The F/W400 Buffalo drives both reported about the same: ~26MB/s read and 16mS access.

By way of comparison, the internal drive reported ~105 MB/s read and 14mS access. [Somewhat interestingly, it's read times increased significantly as it read from 0% to 100% - From about 120 MB/s down to around 30..... This didn't happen at all with the external drive.]

I guess I'll format the other as "Linux Raid" and see what happens from there....... 

Cheers,
Ian

---

