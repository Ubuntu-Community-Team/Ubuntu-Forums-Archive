---
title: "Growing raid"
date: 2009-08-29
forum: General Help
---

### Post by whaase on 2009-08-29
I followed the Linux Raid Wiki to a T on growing a raid. I'm glad it was on a test system lol

Here is what I did.

Made 5 - 15gig partitions.

Built a raid 5 with 4 of them

Got it all mounted and working.

Then issued these commands

mdadm --add /dev/md0 /dev/sdf1

mdadm: added /dev/sdf1



mdadm --grow --raid-devices=5 /dev/md0

mdadm: Need to backup 48K of critical section..

mdadm: ... critical section passed.

Then the final command

resize2fs /dev/md0

resize2fs 1.41.3 (12-Oct-2008)

The filesystem is already 11795616 blocks long.  Nothing to do!




The raid should be 60gig usable (or so) with 5 disks. I'm still showing 45gig. For some reason the FS will not "grow"

Any ideas what I might have missed?

---

### Post by whaase on 2009-08-29
Nevermind. Google was my friend today

---

