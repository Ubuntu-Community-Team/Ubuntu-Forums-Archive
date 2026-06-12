---
title: "raid broke after upgrade"
date: 2009-10-28
forum: General Help
---

### Post by eppo on 2009-10-28
i upgraded my server from 8.10 to 9.04 and after reboot my raid array will not mount. here is the output of sudo mdadm --assemble -f --scan:
mdadm: WARNING /dev/sde1 and /dev/sdc1 appear to have very similar superblocks.
      If they are really different, please --zero the superblock on one
      If they are the same or overlap, please remove one from the
      DEVICE list in mdadm.conf.
and when i do that i get this in dmesg:
[40561.709613] EXT4-fs: unable to read superblock
[40932.360045] md: md0 stopped.
[40932.360059] md: unbind<sdb1>
[40932.393855] md: export_rdev(sdb1)
[40932.394009] md: unbind<sde1>
[40932.423764] md: export_rdev(sde1)
[40932.423919] md: unbind<sda1>
[40932.453763] md: export_rdev(sda1)
[40932.453904] md: unbind<sdd1>
[40932.483763] md: export_rdev(sdd1)
[40932.499065] md: bind<sdd1>
[40932.699589] md: bind<sdc1>

anyone have any idea on how to get this working again?
thanks

---

