---
title: "Problem with mounting second HDD"
date: 2006-02-01
forum: General Help
---

### Post by inew on 2006-02-01
I'm only a beginner in Linux. I installed the Ubuntu 5.10 “The Breezy Badger” just yesterday and I have tried to mount the second HDD (/dev/hdc) with two NTFS partitions on it:

```
sudo fdisk -l
Disk /dev/hdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       17847   143355996    7  HPFS/NTFS
/dev/hdc2           17848       20022    17470687+   f  W95 Ext'd (LBA)
/dev/hdc5           17848       20022    17470656    7  HPFS/NTFS

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9634    77385073+  83  Linux
/dev/sda2            9635       10011     3028252+   f  W95 Ext'd (LBA)
/dev/sda5            9635       10011     3028221   82  Linux swap / Solaris
```

```
sudo hdparm -i /dev/hdc

/dev/hdc:

 Model=HDT722516DLAT80, FwRev=V43OA40A, SerialNo=VD271ATCC2DL6A
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=51
 BuffType=DualPortCache, BuffSize=7674kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 *udma3 udma4 udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: Reserved:

 * signifies the current active mode
```

While mounting I got this error:

```
sudo mount /dev/hdc1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: special device /dev/hdc1 does not exist
```

Also, when I boot it shows something like *“Buffer I/O error on device hdc, logical block 0”*.

I am using this partition in Windows XP with no problems, and scandisk don't find any problems. 

Please can anyone advise how to fix this problem? Thanks a lot!

---

### Post by Jedeye on 2006-02-01
try this guide, it got me working [http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

hope that helps

---

### Post by audax321 on 2006-02-01
Although this might not be your problem, and I hope it isn't. But I used to get that I/O error on my old laptop for a long time and my laptop sometimes used to just lockup and make this strange noise like it was trying to access the hard drive but couldn't. Anyway, a while later the hard drive failed :(

---

### Post by inew on 2006-02-01
[QUOTE=Jedeye]try this guide, it got me working [http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

hope that helps[/QUOTE]

I do all steps with this guide and at the final step I got the error message.

---

### Post by inew on 2006-02-01
[QUOTE=audax321]Although this might not be your problem, and I hope it isn't. But I used to get that I/O error on my old laptop for a long time and my laptop sometimes used to just lockup and make this strange noise like it was trying to access the hard drive but couldn't. Anyway, a while later the hard drive failed :([/QUOTE]

As I have wrote, I have no indications that the drive is going to fail. I'm using it in Windows with no problems/errors, no strange sound. The drive is only half year old.

---

