---
title: "Can't mount Intel raid array"
date: 2009-10-20
forum: General Help
---

### Post by AaronLS on 2009-10-20
I have 3 drives in a RAID 0 array using Intel's MAtrix RAID ICH7R controller(integrated into motherboard).  My Windows OS installed on the array has hosed itself, and I am now booting into an Ubuntu 9.04 LiveCD.  I would like to try and mount the raid 0 array so I can grab some data from the drive before I wipe them(was just a big single partition).  This is the closest I've gotten but I get an error when trying to mount it:

```
admin@ubuntu:/dev$ sudo dmraid -r
/dev/sdc: isw, "isw_dhbaceieab", GROUP, ok, 488397165 sectors, data@ 0
/dev/sdb: isw, "isw_dhbaceieab", GROUP, ok, 488397165 sectors, data@ 0
admin@ubuntu:/dev$ sudo mount /dev/sdc /media/raidone
mount: unknown filesystem type 'isw_raid_member'
```

---

