---
title: "FakeRAID rebuild?"
date: 2010-01-05
forum: General Help
---

### Post by 3vi1 on 2010-01-05
I've got a problem with my 9.10 system:  When I upgraded the BIOS on my Gigabyte EP45-UD3P motherboard, it reset all the BIOS options and broke my RAID1 array.  Unfortunately, I didn't notice this until it had booted once.

I re-enabled RAID in the BIOS, and the BIOS screen now shows the array (with both member disks) in a "REBUILD" status.

There is no way to rebuild the array from the BIOS, but I can't seem to get dmraid to do it either.  dmraid acts as if it doesn't see /dev/sdb as a free drive.

Any pointers as to what I'm doing wrong?

evil@mars:~$ sudo dmraid -ay
ERROR: isw: Could not find disk /dev/sdb in the metadata
ERROR: isw device for volume "Mars-BOOT-R1" broken on /dev/sda in RAID set "isw_decjbijcge_Mars-BOOT-R1"
ERROR: isw: wrong # of devices in RAID set "isw_decjbijcge_Mars-BOOT-R1" [1/2] on /dev/sda
RAID set "isw_decjbijcge_Mars-BOOT-R1" already active
RAID set "isw_decjbijcge_Mars-BOOT-R11" already active
RAID set "isw_decjbijcge_Mars-BOOT-R15" already active

evil@mars:~$ sudo dmraid -s
ERROR: isw: Could not find disk /dev/sdb in the metadata
ERROR: isw device for volume "Mars-BOOT-R1" broken on /dev/sda in RAID set "isw_decjbijcge_Mars-BOOT-R1"
ERROR: isw: wrong # of devices in RAID set "isw_decjbijcge_Mars-BOOT-R1" [1/2] on /dev/sda
*** Group superset isw_decjbijcge
--> Active Subset
name   : isw_decjbijcge_Mars-BOOT-R1
size   : 1465143552
stride : 128
type   : mirror
status : broken
subsets: 0
devs   : 1
spares : 0

evil@mars:~$ sudo fdisk -l                                                                                   

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b988

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       89721   720683901   83  Linux
/dev/sda2           89722       91200    11880067+   5  Extended
/dev/sda5           89722       91200    11880036   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b988

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       89721   720683901   83  Linux
/dev/sdb2           89722       91200    11880067+   5  Extended
/dev/sdb5           89722       91200    11880036   82  Linux swap / Solaris


evil@mars:~$ sudo dmraid -R isw_decjbijcge_Mars-BOOT-R1
ERROR: isw: Could not find disk /dev/sdb in the metadata
ERROR: isw device for volume "Mars-BOOT-R1" broken on /dev/sda in RAID set "isw_decjbijcge_Mars-BOOT-R1"
ERROR: isw: wrong # of devices in RAID set "isw_decjbijcge_Mars-BOOT-R1" [1/2] on /dev/sda              
Rebuild: a hot-spare drive not found for a volume: "isw_decjbijcge_Mars-BOOT-R1". Need a drive to rebuild a volume.

evil@mars:~$ sudo dmraid -R isw_decjbijcge_Mars-BOOT-R1 /dev/sdb
ERROR: isw: Could not find disk /dev/sdb in the metadata
ERROR: isw device for volume "Mars-BOOT-R1" broken on /dev/sda in RAID set "isw_decjbijcge_Mars-BOOT-R1"
ERROR: isw: wrong # of devices in RAID set "isw_decjbijcge_Mars-BOOT-R1" [1/2] on /dev/sda
ERROR: isw: only one failed disk supported
metadata fmt update failed

evil@mars:~$ sudo dmraid -rD
ERROR: isw: Could not find disk /dev/sdb in the metadata
/dev/sda: isw, "isw_decjbijcge", GROUP, ok, 1465149166 sectors, data@ 0

evil@mars:~$ sudo dmraid -n /dev/sdb
ERROR: isw: Could not find disk /dev/sdb in the metadata
no raid disks and with names: "/dev/sdb"
evil@mars:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=WDC, FwRev=30.04G30, SerialNo=WD-WCAPT0808867
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

evil@mars:~$ apt-cache policy dmraid
dmraid:
  Installed: 1.0.0.rc15-11ubuntu3
  Candidate: 1.0.0.rc15-11ubuntu3
  Version table:
 *** 1.0.0.rc15-11ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by 3vi1 on 2010-01-05
I thought I had figured it out... but this didn't work either:

evil@mars:~$ sudo dmraid -f isw -S isw_decjbijcge_Mars-BOOT-R1 -M /dev/sdb
ERROR: isw device for volume "Mars-BOOT-R1" broken on /dev/sda in RAID set "isw_decjbijcge_Mars-BOOT-R1"
ERROR: isw: wrong # of devices in RAID set "isw_decjbijcge_Mars-BOOT-R1" [1/2] on /dev/sda
ERROR: name isw_decjbijcge_Mars-BOOT-R1 is longer than 15 chars

---

### Post by 3vi1 on 2010-01-05
Never could get it to work right...

I ended up recreating a fresh array and installing from scratch.  I'll revisit this when I have more time.

---

