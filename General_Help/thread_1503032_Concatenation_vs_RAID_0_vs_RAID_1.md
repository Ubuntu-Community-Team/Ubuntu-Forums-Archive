---
title: "Concatenation vs RAID 0 vs RAID 1"
date: 2010-06-06
forum: General Help
---

### Post by ShakeyJake on 2010-06-06
Heys, I currently have my '/' on an SSD and my /home on a WD 1.5TB Green Drive. I also have another, exact same WD 1.5TB Greend Drive and a Samsung 500GB that I have rescued from various pcs.

What I would like to do is install my /home to the 500GB drive and then use the two 1.5TB drives for storage in the same machine. I'm doing this because I need more storage space so I'd prefer to avoid RAID 1 for the two drives. I know it's safer and stuff but everything that's important will be on either my /home disk, an external disk or both AS WELL as on the storage drives, so I don't feel like I need the extra safety of RAID 1 on them. What I do need is the space.

RAID 0 has the disadvantage of one drive failing ruining the whole array, does JBOD have the same issue? Is there any way I can just span the two disks into one disk? And then if one fails I lose whatever was on the disk but not the other? Would lvm allow me to do that?

Isn't this called 'linear mode' or something? Are there any tools in ubuntu that would allow me to that? I can find a couple that look right, I just would prefer to still be able to use one of the disks if the other fails and the literature is ambiguous on this.


Thanks guys.

---

### Post by sdennie on 2010-06-06
The problem you are going to have is with the "meta-data".  If you create a filesystem that is spanning multiple disks, if one of those disks becomes unavailable, the filesystem is now in a bad state even if you have perfectly reasonable data sitting on the working disks.

I would honestly just go with RAID0 and buy an external drive to back it up.  The other option is to not use any RAID/lvm solution and just mount the disks to two different places.

---

### Post by ShakeyJake on 2010-06-06
Yeah the thought of just mounting the two disks seperately did occur to me, it just feels a bit . . . . .untidy, I dunno. RAID 0 is sounding better too.

---

