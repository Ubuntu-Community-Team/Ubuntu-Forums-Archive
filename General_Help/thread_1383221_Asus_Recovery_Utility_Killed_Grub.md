---
title: "Asus Recovery Utility Killed Grub?"
date: 2010-01-17
forum: General Help
---

### Post by Econ on 2010-01-17
I've been searching all day for something related to this, but everything I found is related to XP installs on Ubuntu-only systems or re-installation of XP on dual boots.

I've been running a dual-boot XP/Ubuntu 9.04 NR system for a couple months.  I'm primarily using Ubuntu, but have to keep XP around for life admin programs (like budgeting, etc) that aren't Linux compatible.  I have an Asus Eee 1000-HB (don't ask) that came with XP pre-installed.

The last time I was using XP, I think the system ran a series of updates and needed to restart after completion.  As it was ages ago, I can't remember for sure, but I think it's possible that XP went into hibernate at that point instead of shutting down.

When I tried to bring up XP this morning, I was diverted to an Asus recovery utility.  It did a bit of seeking on the HDD and then presented me with an OK/Cancel dialog box.  I hit cancel and rebooted.

Then everything went wrong.  Grub failed to load and dumped me to grub rescue>.  I tried 'set root' to each of the partitions 'ls' was showing, but the grub default was to a partition (0,6) that 'ls' doesn't see any longer.  Partition 0 through 0,5 all come back with a "format not recognized" error.

I'm running on a Ubuntu live CD right now (on the upside, I finally had an excuse to buy an external DVD burner I wanted).  I can't get to the XP partition as the volume fails to mount.  It gives me an error code 14, stating that the partition is still in hibernate and needs to be brought out by XP or forced out by Ubuntu.  This, of course, still doesn't fix the problem of the missing partition.

Everything important is backed up on the NAS, but I'd really like to avoid wiping and restarting.  Anyone have any ideas?

Sorry for the verbose post.  Thanks for any help you can provide. (And apologies for any spelling errors - I prefer dvorak over qwerty and this livecd thing is killing my wpm)

---

