---
title: "dmraid or mdadm ?"
date: 2012-02-13
forum: General Help
---

### Post by YannBuntu on 2012-02-13
Dear all

**How can we know the type (dmraid or mdadm) of a RAID? **

For example, if you see this:
```
~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/mapper/isw_ecachjgbgg_RAID-0p1: LABEL="SYSTEM" UUID="AA3826BE38268981" TYPE="ntfs"
/dev/mapper/isw_ecachjgbgg_RAID-0p2: UUID="DC0C1C3B0C1C135E" TYPE="ntfs"
/dev/mapper/isw_ecachjgbgg_RAID-0p3: LABEL="HP_TOOLS" UUID="89A4-A330" TYPE="vfat"
/dev/sda: TYPE="isw_raid_member"
```

do you know if this system needs to activate dmraid or mdadm ? if yes, which clue do you use?

---

