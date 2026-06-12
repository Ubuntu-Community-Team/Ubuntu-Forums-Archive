---
title: "USB HDD Spins right back up after being spun down - mount.ntf lock"
date: 2011-02-09
forum: General Help
---

### Post by equinox102 on 2011-02-09
Sorry if I have posted this in the wrong section for this is my first post here.

I'm pretty new to Linux (I've dabbled over the years but I'd still call myself a novice)

I've put together a HTPC running Ubuntu Minimal.  The hardware is a net-top and hence needs external hard drives to have any significant capacity.

I have an Iomega 1TB 3.5" USB2.0 external drive formatted with a single NTFS partition hooked up to hold extra content however it is only used for an hour or two per day.  Being an external hard drive I'd imagine it was never designed to be spinning 24/7 and I'd like to spin it down when not in use.

The problem is I'd like it to remain mounted so that applications can use it when they want (after waiting for it to spin back up).  I can get the drive to spin down with this command:

sdparm --flexible --command=stop /dev/sdX &>/dev/null

However it instantly spins back up.  I ran fuser -m /dev/sdb1 and it  says that the process mount.ntf is using the drive.  The thing is no data appears to be being accessed at all; it's just mounted.

Is there any way to get the drive to spin down while still mounted?

Thanks in advance!

---

