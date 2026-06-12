---
title: "used partimage, deleted old ext3 partition and restored image"
date: 2006-06-03
forum: General Help
---

### Post by d3wu on 2006-06-03
I used partimage to back up my root partition, deleted the root partition (3.6 gigs) and formatted a new ext3 partition of 9 gigs.

My old root partition was 2.6 gigs used, 1 gig free, so the partimage file was 2.6 gigs (not compressed).   I restored the partimage file onto the new ext3 partition with 9 gigs.

I log into kubuntu fine, but the OS still sees only 1 gig free.  Is there a simple way to have the OS know it has an additional ~6 gigs?  Any suggestions would help!  Thanks

---

### Post by d3wu on 2006-06-04
so i figured it out - i first used e2fsck to check the partition

e2fsck -f /dev/hda3

then i just used resize2fs.  worked perfectly:

resize2fs -p /dev/hda3 9G

:)

---

