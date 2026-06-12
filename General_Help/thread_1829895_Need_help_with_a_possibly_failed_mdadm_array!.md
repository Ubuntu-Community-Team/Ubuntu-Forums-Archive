---
title: "Need help with a possibly failed mdadm array!"
date: 2011-08-20
forum: General Help
---

### Post by raidedguy on 2011-08-20
So I have a server with 15*1.5TB Hard drives which are configured as 1 raid6 array in mdadm.  This last weekend the unthinkable happened, 3 drives failed (we think the card they were on overheated).  After powering down for a few hours all 15 drives came back online and were readable, however, mdadm refused to mount the array as 3 of the drives were out of sync.  It would only assemble the array with 12 of the 15 drives and refuse to start.  After playing around with it for a few hours I did what has worked before on raid0 arrays,
  
  mdadm --create /dev/md0 --assume-clean -l6 -n15 /dev/sd[b-p]

It complained that all 15 drives were already part of an array and i (somewhat stupidly) said continue anyway.  I then tried to mount the array and received a "bad superblock" warning.  I let xfs tools try and repair the filesystem, but after several hours it hadn't found a working superblock.  I have since had 1 drive show up as failed again.

Is there any command or program that might save me from losing all this data?  The data should still be on the disks untouched, I've only modified the superblocks.  Furthermore, this is array is not written to very often, it's almost guaranteed to of failed during a read.

Any help would be appreciated, Thank you.

---

