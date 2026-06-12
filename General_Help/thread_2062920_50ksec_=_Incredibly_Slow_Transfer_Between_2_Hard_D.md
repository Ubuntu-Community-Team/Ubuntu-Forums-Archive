---
title: "50k/sec = Incredibly Slow Transfer Between 2 Hard Drives"
date: 2012-09-26
forum: General Help
---

### Post by Andrew F in Australia on 2012-09-26
Hi All,

Broken something here that I can't find.  Hard drives are  working at an internal transfer rate of 50k/sec - not a typo - 50000  bytes/sec

Copying files from the Nautilus file panel between 2 hard drives (was 1GB, gave up and used Window$)

Format shifting more music today from CD to hard drive, took 14:50 sec to copy 41MB = 46kB/sec.  Used eac under WINE to do this

Re-checked by burning the CD under Rubyripper with 3x sampling, took 8 minutes

Appreciate help please if anyone can do so.

output from fstab etc below
------------------------------------
History

I  had a power outage mid update of a new linux kernel that killed the  machine. A network administrator and Certified Linux ...... person that I  know couldn't save it.

Have had to start from scratch/reinstall Win 7 and Ubuntu 12.04 on a machine as a dual boot.

Finally reinstalled it Mon.

Run sda = 750MB drive full of music files
sdb = 750MB drive for operating systems/data storage
sdc = 2000MB drive with about 150MB of music files onto it.

-------------------------------------

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb5 :
/dev/disk/by-uuid/---snip out code----/    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb7 :
/dev/disk/by-uuid/---snip out code----[/B]/media/Data    ntfs-3g    rw,auto,users,exec,sync,locale=en_AU.UTF-8    0    0
#Entry for /dev/sdb1 :
/dev/disk/by-uuid/---snip out code----[/B]/media/Windows    ntfs-3g    rw,auto,users,exec,sync,locale=en_AU.UTF-8    0    0
#Entry for /dev/sda1 :
/dev/disk/by-uuid/---snip out code----[/B] /media/music    ntfs-3g    rw,auto,users,exec,sync,nosuid,nodev,locale=en_AU.UTF-8    0    0
#Entry for /dev/sdc1 :
/dev/disk/by-uuid/---snip out code----[/B]/media/music2    ntfs-3g    rw,auto,users,exec,sync,nosuid,nodev,locale=en_AU.UTF-8    0    0
#Entry for /dev/sdb6 :
/dev/disk/by-uuid/---snip out code----[/B]    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


```

```
 horace-music@horacemusic-System-Product-Name:~$ sudo hdparm -i /dev/sda
[sudo] password for horace-music: 

/dev/sda:

 Model=WDC WD7500AACS-00C7B0, FwRev=01.01B01, SerialNo=WD-WCASN0028719
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

``````

horace-music@horacemusic-System-Product-Name:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=WDC WD7500AACS-00C7B0, FwRev=01.01B01, SerialNo=WD-WCASN0028725
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
``````

horace-music@horacemusic-System-Product-Name:~$ sudo hdparm -i /dev/sdc

/dev/sdc:

 Model=WDC WD20EARX-00PASB0, FwRev=51.0AB51, SerialNo=WD-WCAZAD616115
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
```
horace-music@horacemusic-System-Product-Name:~$ sudo hdparm -Tt /dev/sda && sudo hdparm -Tt /dev/sdb && sudo hdparm -Tt /dev/sdc

/dev/sda:
 Timing cached reads:   2334 MB in  2.00 seconds = 1167.11 MB/sec
 Timing buffered disk reads: 224 MB in  3.03 seconds =  74.01 MB/sec

/dev/sdb:
 Timing cached reads:   2396 MB in  2.00 seconds = 1198.16 MB/sec
 Timing buffered disk reads: 198 MB in  3.03 seconds =  65.42 MB/sec

/dev/sdc:
 Timing cached reads:   2336 MB in  2.00 seconds = 1167.91 MB/sec
 Timing buffered disk reads: 314 MB in  3.00 seconds = 104.51 MB/sec
horace-music@horacemusic-System-Product-Name:~$
```

Any help you could provide would be greatly appreciated

Regards,

Andrew F

---

### Post by HiImTye on 2012-09-26
is it just as slow in the command line, for instance, using rsync -P ?

---

### Post by Andrew F in Australia on 2012-09-26
> **HiImTye said:**
> is it just as slow in the command line, for instance, using rsync -P ?

I'll just test it out and see - brb.

Oh - the drives work a lot faster in Windows too, so it's something Linux/Ubuntu specific.

Thanks again,

AF

---

### Post by Andrew F in Australia on 2012-09-26
> **HiImTye said:**
> is it just as slow in the command line, for instance, using rsync -P ?

3.6MB/sec, copying on to the same disk

Ta

---

### Post by HiImTye on 2012-09-26
that's what I suspected. nautilus seems to get lots of reports of slow transfers for various things. I tend to just use the CLI to avoid all the hassle

---

### Post by Andrew F in Australia on 2012-09-26
> **HiImTye said:**
> that's what I suspected. nautilus seems to get lots of reports of slow transfers for various things. I tend to just use the CLI to avoid all the hassle

Thanks HilmTye.

I wouldn't have thought that the WINE emulator would have done it, burning a disk from the CD to a drive.

The settings that I have are as best as I can tell the same as when it used to take 3 minutes to burn a CD.

Anything else that I might check in the configuration side of things (transfer rate cap???) to try and get it working again?

Cheers,

AF

---

### Post by HiImTye on 2012-09-26
I'm not sure, as far as I know transfer caps are kernel problems. nautilus just tends to be slow for whatever reason

---

### Post by dcstar on 2012-09-26
> **Andrew F in Australia said:**
> 
...........
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb5 :
/dev/disk/by-uuid/---snip out code----/    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb7 :
/dev/disk/by-uuid/---snip out code----/media/Data    ntfs-3g    rw,auto,users,exec,**sync**,locale=en_AU.UTF-8    0    0
#Entry for /dev/sdb1 :
/dev/disk/by-uuid/]---snip out code----/media/Windows    ntfs-3g    rw,auto,users,exec,**sync**,locale=en_AU.UTF-8    0    0
#Entry for /dev/sda1 :
/dev/disk/by-uuid/---snip out code---- /media/music    ntfs-3g    rw,auto,users,exec,**sync**,nosuid,nodev,locale=en_AU.UTF-8    0    0
#Entry for /dev/sdc1 :
/dev/disk/by-uuid/---snip out code----/media/music2    ntfs-3g    rw,auto,users,exec,**sync**,nosuid,nodev,locale=en_AU.UTF-8    0    0
#Entry for /dev/sdb6 :
/dev/disk/by-uuid/---snip out code----    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0

```


[LIST=1]
[*]No one cares what your disks UUIDs are.
[*]Stop highlighting EVERYTHING, highlighting is for specific things that need **HIGHLIGHTING**.
[*]You are forcing Synchronous writes to the drives, that always slows things down.
[*]Linux file I/O to foreign filesystems is always slower than native Linux filesystems.
[/LIST]

---

### Post by Andrew F in Australia on 2012-09-26
> **dcstar said:**
> 
[LIST=1]
[*]No one cares what your disks UUIDs are.
[*]Stop highlighting EVERYTHING, highlighting is for specific things that need **HIGHLIGHTING**.
[*]You are forcing Synchronous writes to the drives, that always slows things down.
[*]Linux file I/O to foreign filesystems is always slower than native Linux filesystems.
[/LIST]


Hi David,

The highlighting went on by accident, I thought it was part of the code box.

**Thankyou** for pointing out 3.  I'll change and see if it behaves differently then report back

The system's hanging at the moment waiting for data at times on anything that's resource intensive.

Cheers,

AF

---

### Post by Andrew F in Australia on 2012-09-26
> **Andrew F in Australia said:**
> 
**Thankyou** for pointing out 3.  I'll change and see if it behaves differently then report back
Cheers,

AF

Thanks, David,  got it fixed.

Works as it used to with async, not sync, as a setting in the fstab file.

Cheers,

AF

---

### Post by dcstar on 2012-09-27
> **Andrew F in Australia said:**
> Thanks, David,  got it fixed.

Works as it used to with async, not sync, as a setting in the fstab file.

Cheers,

AF

The Sync option should only be used with things like Floppy - or other removable - media as it forces a total flush of every sector of data written to the device.

As you discovered, it cripples throughput and is not really a good idea unless you demand data integrity over everything else.

---

