---
title: "Gparted crashes during scanning of disks/startup"
date: 2010-11-05
forum: General Help
---

### Post by RaZoR1394 on 2010-11-05
> 
§sudo gparted

======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...


The disk that gets scanned last is /dev/sdm

> 
§sudo fdisk -l

Disk /dev/sdf: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x0005c5a7

    Enhet Start     Början        ****     Block    Id  System
/dev/sdf1   *           1          13      102400    7  HPFS/NTFS
Partition 1 slutar inte på cylindergräns.
/dev/sdf2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdg: 74,4 GB, 74355769344 byte
255 huvuden, 63 sektorer/spår, 9039 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x7521d8dc

    Enhet Start     Början        ****     Block    Id  System
/dev/sdg1               1        9040    72611840    7  HPFS/NTFS

Disk /dev/sdi: 500,1 GB, 500107862016 byte
255 huvuden, 63 sektorer/spår, 60801 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x000501ab

    Enhet Start     Början        ****     Block    Id  System
/dev/sdi1               1       59272   476097536   83  Linux
/dev/sdi2           59272       60802    12286977    5  Utökad
/dev/sdi5           59272       60802    12286976   82  Linux växling / Solaris

Disk /dev/sdh: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x000bb9f3

    Enhet Start     Början        ****     Block    Id  System
/dev/sdh1               1      120380   966943744   83  Linux
/dev/sdh2          120380      121602     9816064+   5  Utökad
/dev/sdh5          120380      121602     9816064   82  Linux växling / Solaris

Disk /dev/sdk: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x519dd4f7

    Enhet Start     Början        ****     Block    Id  System
/dev/sdk1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdj: 74,4 GB, 74355769344 byte
255 huvuden, 63 sektorer/spår, 9039 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x000b8663

    Enhet Start     Början        ****     Block    Id  System
/dev/sdj1               1        8666    69606400   83  Linux
/dev/sdj2            8666        9040     3004417    5  Utökad
/dev/sdj5            8666        9040     3004416   82  Linux växling / Solaris

Disk /dev/sdm: 500,1 GB, 500107862016 byte
255 huvuden, 63 sektorer/spår, 60801 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0x02f702f7

    Enhet Start     Början        ****     Block    Id  System
/dev/sdm1   *           1          64      512000   83  Linux
Partition 1 slutar inte på cylindergräns.
/dev/sdm2              64       60802   487873536   8e  Linux LVM


/dev/sdm contains Sabayonlinux Gnome 5.4 and the problems started about the time after I installed the OS.

Do I have to delete the OS or is there another way? BTW this disk with Sabayon cannot be seen from bios even though the disk is healthy and connected to the motherboard. The problem started some weeks ago.

---

