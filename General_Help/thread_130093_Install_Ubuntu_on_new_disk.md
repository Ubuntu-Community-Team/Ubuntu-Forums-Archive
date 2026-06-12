---
title: "Install Ubuntu on new disk"
date: 2006-02-15
forum: General Help
---

### Post by bigblop on 2006-02-15
I have a new 80 GB disk that I would like to install Ubuntu on.

I have just inserted the Install CD and then I come to the partitioning of disks I choose the free space.

Then I get a list of what is going to happen:

Partition #1 on IDE1 Master (hda) as ext3
Partition #5 on IDE1 Master (hda) as swap


but why does it use #5 for swap and not #2?? Is that normal?

---

### Post by cotcot on 2006-02-15
It is normal that swap is not hda2. You can make up to 4 primary partitions. The numbering for this is reserved as hda1 to hda4 even if you do not have 4. Swap is a non-primary partition so the numbering starts after the primary partition reserved number. The first non-primary partition is hda5. If you make a lofical partition it will also have a number above hda4.

---

### Post by au010900 on 2008-07-12
Guys,

I am trying to install a new disk. I have managed to mount the drive, how do i make it active?

Regards,

Dave

---

