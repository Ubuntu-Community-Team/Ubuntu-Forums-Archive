---
title: "System crashed, mounting Ubuntu full disk encrypted filesystem"
date: 2011-01-14
forum: General Help
---

### Post by c289 on 2011-01-14
I have a crashed installation which was encrypted with the standard full disk encryption from the Ubuntu alternate install CD.

The drive is fine per SMART.

I'm trying to mount this from the live CD to do some data recovery. At this point, it's not important why the system crashed. I'm planning to mount it, evacuate the data, and reinstall.

The drive is fine because it shows the unencrypted /boot

The live CD won't mount the main data partition. It's trying to mount the whole disk, which obviously won't fly as the whole disk is an LVM group.

The drive on which the crashed system resides is /dev/sdb

I have unlocked sdb5 (the main data partition) through the Ubuntu disk manager on the live CD by inputting the correct password (more evidence this isn't a disk issue). Below the unlocked sdb5 the disk manager is showing a LVM2 physical volume as /dev/dm-0

Any ideas on mounting /dev/dm-0 as something readable from which data can be copied?

---

