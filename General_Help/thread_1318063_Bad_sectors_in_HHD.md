---
title: "Bad sectors in HHD"
date: 2009-11-07
forum: General Help
---

### Post by dox_drum on 2009-11-07
Hi people, Since last week, when I installed Karmic, an icon appears in the upper bar saying that my HHD has many bad sectors.

It is supposed that 
```
sudo fsck /dev/sdb/
```
would do the repair, but it said that the disk is mounted.

A frind of mine told me that it must be done from the recovery-mode (in GRUB), but still when I choose the root terminal it said the disk is mounted.

What should I do?

Thank you.

---

### Post by lloyd_b on 2009-11-07
'fsck' will NOT fix bad sectors.  For the most part, *nothing* will fix them.

A bad sector can result from a number of causes.  For instance, if there's a defect in the coating on the disk itself.  This type of problem can't be fixed, but you can "map out" those bad sectors, and keep using the drive.

But, if a drive starts developing *new* bad sectors, then it's a warning that the drive is starting to fail.  In which case, it should be replaced ASAP!

Lloyd B.

---

### Post by whoop on 2009-11-07
Backup all your important data first (which you should have done allready), install smartmontools. Make it do a long test (look here for tutorial: [http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)).

If it really has bad sectors, I would suggest replacing the drive immediately.

---

