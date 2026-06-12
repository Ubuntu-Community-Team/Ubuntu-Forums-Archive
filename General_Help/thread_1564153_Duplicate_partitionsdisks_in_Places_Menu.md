---
title: "Duplicate partitions/disks in Places Menu"
date: 2010-08-30
forum: General Help
---

### Post by s_g_robertson on 2010-08-30
I've got a strange situation where my two additional internal disks are showing up twice in the places menu.  It's not really causing a problem but something is clearly not correct.

If I try and select the "500G" from the places menu that has the icon that looks most like a disk(same as the desktop icon) then it opens correctly.  If I try the other "500G" option then I get the error dialog attached.

Any clues?

Thanks

Stephen

```
# /etc/fstab: static file system information.
#
# <file system>                                 <mount point>   <type>  <options>                       <dump>  <pass>
proc                                            /proc           proc    defaults                        0       0
# /dev/sda1
UUID=f59f1f48-b8ec-489c-b634-fe85c740055a       /               ext3    relatime,errors=remount-ro      0       1
# /dev/sda5
UUID=3c18821b-0b65-443e-9007-b364c693c151       none            swap    sw                              0       0
UUID=54c813f4-2ebe-4b9b-bc92-66c40bb154d1       /media/500G     ext3    rw,user,auto,noatime            0       0
UUID=664f9035-a206-4238-8cd8-ac3d5616c622       /media/disk     ext3    rw,user,auto,noatime                    0       0

/dev/scd0                                       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8       0       0
/dev/fd0                                        /media/floppy0  auto    rw,user,noauto,exec,utf8        0       0

```

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020928

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a64dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9588    77015578+  83  Linux
/dev/sdc2            9589        9964     3020220    5  Extended
/dev/sdc5            9589        9964     3020188+  82  Linux swap / Solaris

```

---

