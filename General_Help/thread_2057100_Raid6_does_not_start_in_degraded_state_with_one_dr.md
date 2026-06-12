---
title: "Raid6 does not start in degraded state with one drive failing"
date: 2012-09-13
forum: General Help
---

### Post by PavelMan on 2012-09-13
At boot time I get a question if I want to start it in defraded state. I say "y", and still get this:
> 
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
[26.065844] bio: create slab <bio-1> at 1
[26.065906] md: personality for level is not loaded!
mdadm: failed to start array /dev/md0: invalid argument
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: /dev/md0 is already in se.
Could not start the RAID in degraded mode.
Dropping to a shell.


my mdadm.conf says
> 
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR [email]xxx@gmail.com[/email]
ARRAY /dev/md0 UUID=953a0832:59d3922f:c3b7e12c:0dda0868


needless to say, mdadm -D /dev/md0 says "does not appear to be active". But the funny thing is that remaining drives appear as spares...

> /dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 953a0832:59d3922f:c3b7e12c:0dda0868
           Name : sphynx:0  (local to host sphynx)
  Creation Time : Wed May  2 19:32:14 2012
     Raid Level : -unknown-
   Raid Devices : 0
 Avail Dev Size : 3900700672 (1860.00 GiB 1997.16 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 64ba297a:f73ede16:975d6411:fbf2dcae
    Update Time : Wed Sep 12 21:38:51 2012
       Checksum : ac1d544 - correct
         Events : 1
   Device Role : spare
   Array State :  ('A' == active, '.' == missing)

/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 953a0832:59d3922f:c3b7e12c:0dda0868
           Name : sphynx:0  (local to host sphynx)
  Creation Time : Wed May  2 19:32:14 2012
     Raid Level : -unknown-
   Raid Devices : 0
 Avail Dev Size : 3900700672 (1860.00 GiB 1997.16 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 18d85a16:30978466:0a0e2192:50e3d7fc
    Update Time : Wed Sep 12 21:38:51 2012
       Checksum : c550ebfa - correct
         Events : 1
   Device Role : spare
   Array State :  ('A' == active, '.' == missing)

/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 953a0832:59d3922f:c3b7e12c:0dda0868
           Name : sphynx:0  (local to host sphynx)
  Creation Time : Wed May  2 19:32:14 2012
     Raid Level : -unknown-
   Raid Devices : 0
 Avail Dev Size : 3900700672 (1860.00 GiB 1997.16 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : b2646441:bf306e17:9dcff561:e84c4e8f
    Update Time : Wed Sep 12 21:38:51 2012
       Checksum : 38f3d4f - correct
         Events : 1
   Device Role : spare
   Array State :  ('A' == active, '.' == missing)


So, when I run mdadm -A /dev/md0 /dev/sd[bcd]1, it says something like "3 spares, 0 drives, not enough stuff"...

Does anybody have any ideas what may be going on?

---

