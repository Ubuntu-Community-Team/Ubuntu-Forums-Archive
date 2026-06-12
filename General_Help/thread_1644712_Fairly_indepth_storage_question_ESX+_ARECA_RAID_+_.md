---
title: "Fairly indepth storage question ESX+ ARECA RAID + 10.10"
date: 2010-12-13
forum: General Help
---

### Post by Cr0n_J0b on 2010-12-13
I'm not sure if anyone can help with this, but thougth I would ask. I'm playing around with a system build using a bunch of SATA disks on an ARECA 1260 array.  The drives are 500 and 750GB SATA from Maxtor, Seagate and Hitachi.  I've setup several (8) volume groups on a RAID set that contains 10 disks.  All the volumes are RAID6.  Each of the volume groups is about 500GB. (464GB actually).

In ESX i took the 500GB volume and created a data store out of it, then put my virtual disk on that for Ubuntu data drive.  so far so good.  I actually created and added 3 of these disks, for the heck of it to check out spanning and striping at the OS.

Once the system got running, I partitioned the first volume /dev/sdb into a 500GB disk /dev/sdb1.  I took that, put ext4 on it and mounted to the root for testing.  I have SAMBA running, so i made a share out of it and then started testing file copies from a Windows 7 host.

I was actually quite surprised to see the performance, (40-50MB/s).  The activity looked a bit odd however, so i've been playing with this.  In my network monitor it looks like there are sharp peaks of 100MB/s and low valleys of 100KB/s in a whipsaw fashion.  I've run tests to other raid systems and they are pretty consistent, flatline mesa for the copy operation, not whipping up and down.

I've tried differnt filesystems zfs, ext3 etc to see if I can figure it out, but nothing is helping.  It feels like the drives aren't synching at the raid controller, but I don't really have a way to check that.

any help would be appreciated

---

