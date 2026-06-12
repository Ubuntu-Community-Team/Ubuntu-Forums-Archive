---
title: "Problems creating Raid 5 array"
date: 2010-08-19
forum: General Help
---

### Post by Godsbrother on 2010-08-19
Hi,

I have 10.4 and am trying to add 3 x Samsung 1TB drives (HD103SJ) connected via a generic SIL-3114 controller (not using raid).

I am using webmin (current version) and when attempting to use mdadm to create a raid 5 array get the following error -

Failed to create RAID : mdadm in --create mode failed :

mdadm: array /dev/md0 started.

Now when you go back and look at the raid array it shows as active but degraded with a failed drive and is recovering.

I can't figure out why?

Anyone got any suggestions......

---

