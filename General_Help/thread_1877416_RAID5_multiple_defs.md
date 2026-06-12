---
title: "RAID5 multiple defs"
date: 2011-11-08
forum: General Help
---

### Post by wvo on 2011-11-08
I've been having probs with a RAID5 filesystem (created with mdadm on 10.04) which freezes the system, then spends the next 12 or so hours resyncing itself.  I had only recently replaced the original disks with larger ones, recreated the RAID5 and was dismayed to see the same behaviour.  With no other avenue open to me, I recreated the RAID5 once again.  I believe I didn't remove the old one properly, coz now I get two definitions for the same device and it won't mount without some fancy dance steps.

# mdadm --examine --scan -v
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=bcb1d8ee:baf8fdb4:576b138c:f9fe661c
   spares=1   devices=/dev/sdd,/dev/sdc,/dev/sdb

ARRAY /dev/md1 level=raid5 num-devices=3 UUID=ba0138e8:a3d3222a:576b138c:f9fe661c
   devices=/dev/sdd1,/dev/sdc1,/dev/sdb1

 The 2nd def is the correct one.  I don't know how it's fallen back to sd[bcd] from sd[bcd]1.  Something I did wrong in the process, I assume.

I'd like to avoid a 3rd re-creation, but I can't figure any way to get rid of the erroneous info nor do I know where it's coming from.   It doesn't come from mdadm.conf or fstab.  "mdadm --examine --scan -v /dev/sd[bcd]1" returns the correct info and UUID. "mdadm --examine --scan -v /dev/sd[bcd]" returns the wrong.

The original problem presented when running Bacula (backups) and then writing something else to the RAID5 filesystem at the same time.  I suspect inadequate hardware that can't deal with the load.

Thanks for any suggestions.

Cheers,
Lyn

---

