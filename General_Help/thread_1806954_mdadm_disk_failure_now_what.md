---
title: "mdadm disk failure: now what?"
date: 2011-07-18
forum: General Help
---

### Post by pieroxy on 2011-07-18
Hi,

I am running an Ubuntu-Server 11.04 box on which I have a RAID5 array of 6 HDDs. I am wondering how I will be able to figure out which drive fails when that happens.

I am sure I can get which *device* fails from whatever logs mdadm will provide. But how will I be able to figure out which physical drive failed so that I can remove it?

---

### Post by psusi on 2011-07-18
Match up the serial number the drive reports with what is on the label.

---

### Post by Habitual on 2011-07-18
```
sudo mdadm --detail /dev/xxN
```

---

### Post by pieroxy on 2011-07-19
> **Habitual said:**
> ```
sudo mdadm --detail /dev/xxN
```

```
pieroxy@server:~$ sudo mdadm --detail /dev/sda1
mdadm: /dev/sda1 does not appear to be an md device

```
So that doesn't work obviously...
I tried --detail on the md array:

```
pieroxy@server:~$ sudo mdadm --detail /dev/md127 
/dev/md127:
        Version : 1.2
  Creation Time : Mon Jul 18 12:18:30 2011
     Raid Level : raid5
     Array Size : 9767552000 (9315.06 GiB 10001.97 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Tue Jul 19 11:10:21 2011
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu-home-server:0  (local to host ubuntu-home-server)
           UUID : 1a40a7a7:f093ce5c:26e0578c:40d9a322
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       6       8       81        5      active sync   /dev/sdf1

```

It hardly gives me any indication of my HDD.

Actually, I just found a way to give me the serial number of a HDD:

```
pieroxy@server:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD20EARS-00MVWB0, FwRev=51.0AB51, SerialNo=WD-WCAZA6106876
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=3907029168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

This way, when a HDD dies I can get through my HDDs one by one and remove the one that failed. Thanks.

---

