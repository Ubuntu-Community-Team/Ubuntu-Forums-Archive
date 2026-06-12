---
title: "Mixing 512 &amp; 4k sector HD's in a software RAID 5 array"
date: 2010-03-24
forum: General Help
---

### Post by frankgg on 2010-03-24
I currently have a mirror raid array with 2x 1TB HD's (Western Digital Caviar Green WD10EADS SATA). They are both the standard 512 byte sector HD's.
 
I just ordered a new 1TB Hard Drive (Western Digital Caviar Green WD10EARS SATA) as I want to wipe the current mirror raid and use the 3 disks in a raid 5 array.
 
But to my suprise, the new 1TB HD is an "advanced format" HD with 4k byte sectors...
 
Am I screwed or can this 4k byte sector HD be used in a software raid 5 array along with the 512 byte sector hard drives?
 
 
(The WD hard drive says you can jumper it to work with XP which can only use 512 byte sectors... there's also a utility you can run that does something to make it compatible with XP too.... Makes me wonder if these new drives are backwards compatible?)

---

### Post by srs5694 on 2010-03-24
These WD drives have 4096-byte physical sectors, but they look just like normal drives with 512-byte sectors to most software, including the Linux kernel and partitioning tools. This is good for compatibility, but it can create a performance problem: If partitions aren't aligned on 4096-byte (8-sector) boundaries, performance can suffer *a lot.* (I've benchmarked performance penalties of up to about 30x on some tests.)

RAID 5 and RAID 6 have their own alignment issues, which typically involve larger values (16 KiB to 256 KiB) and less of a performance hit in case of improper partition alignment.

Overall, if you're careful about partition alignment, you should be fine. Theoretically. I've not actually done this myself, though. I recommend aligning everything on 1 MiB (2048-sector) boundaries, which is becoming the new standard. Unfortunately, you might need to jump through some hoops to get this done, since Linux partitioning tools are only just starting to do this by default. I'm not sure of the exact current status of either the fdisk family or libparted-based tools in this respect, although I believe a shift to 2048-sector alignment is in the pipeline for fdisk. My own [GPT fdisk](http://www.rodsbooks.com/gdisk/) does 2048-sector alignment as of version 0.6.6, but it's intended to create GPT rather than MBR disks. (This may be fine, and even desirable, for many situations, but you'll have to be the judge of that.)

---

