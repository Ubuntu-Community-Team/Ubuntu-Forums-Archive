---
title: "NTFS write speed only 5 megabytes per second - please help"
date: 2010-05-22
forum: General Help
---

### Post by Rev2010 on 2010-05-22
Here's the line from my fstab that auto mounts my NTFS Windows drive:

/dev/sda1       /media/disk     ntfs-3g    defaults,umask=007,gid=46,noatime   0       0

When writing to the drive the max speed I get is 5 megabytes per second. I Googled it and tried some other posted Fstab lines but all disabled my write access for some reason even without "RO" in the line. Can someone please give me some guidance as to how I get the normal Sata HD transfer speed which is more like 55-75 megs or more per second or so? Do I need to set something other than in the fstab? Thanks in advance.


Rev.

---

### Post by Rev2010 on 2010-05-22
And this what the Hdparm readout says:

 Model=ST3500630A                              , FwRev=3.AAC   , SerialNo=            3QG04GYV
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

And SDParm readout:

    /dev/sda1: ATA       ST3500630A        3.AA
    Direct access device specific parameters: WP=0  DPOFUA=0
Read write error recovery [rw] mode page:
  AWRE        1  Automatic write reallocation enabled
  ARRE        0  Automatic read reallocation enabled
  TB          0  Transfer block
  RC          0  Read continuous
  EER         0  Enable early recovery
  PER         0  Post error
  DTE         0  Data terminate on error
  DCR         0  Disable correction
  RRC         0  Read retry count
  COR_S       0  Correction span (obsolete)
  HOC         0  Head offset count (obsolete)
  DSOC        0  Data strobe offset count (obsolete)
  WRC         0  Write retry count
  RTL         0  Recovery time limit (ms)
Caching (SBC) [ca] mode page:
  IC          0  Initiator control
  ABPF        0  Abort pre-fetch
  CAP         0  Caching analysis permitted
  DISC        0  Discontinuity
  SIZE        0  Size enable
  WCE         1  Write cache enable
  MF          0  Multiplication factor
  RCD         0  Read cache disable
  DRRP        0  Demand read retention priority
  WRP         0  Write retention priority
  DPTL        0  Disable pre-fetch transfer length
  MIPF        0  Minimum pre-fetch
  MAPF        0  Maximum pre-fetch
  MAPFC       0  Maximum pre-fetch ceiling
  FSW         0  Force sequential write
  LBCSS       0  Logical block cache segment size
  DRA         0  Disable read ahead
  NV_DIS      0  Non-volatile cache disable
  NCS         0  Number of cache segments
  CSS         0  Cache segment size
Control [co] mode page:
  TST         0  Task set type
  TMF_ONLY    0  Task management functions only
  D_SENSE     0  Descriptor format sense data
  GLTSD       1  Global logging target save disable
  RLEC        0  Report log exception condition
  QAM         0  Queue algorithm modifier
  QERR        0  Queue error management
  RAC         0  Report a check
  UA_INTLCK   0  Unit attention interlocks control
  SWP         0  Software write protect
  ATO         0  Application tag owner
  TAS         0  Task aborted status
  AUTOLOAD    0  Autoload mode
  BTP        -1  Busy timeout period (100us)
  ESTCT      30  Extended self test completion time (sec)

---

### Post by emanuel.b on 2010-05-22
I don't understand. My drive's nominal speed is about 4.5 - 6 MB a seccond. I don't think this is a problem. Unless it was noticeable faster before then slowed down. If so, it sounds like a hardware problem to me.

---

### Post by Rev2010 on 2010-05-22
Actually, I've now tested and found it's this slow also when copying a file in Ubuntu to a different folder (EXT3 filesystem) - under 10 megabytes per second.

@Emanuel, this speed is NOT normal. IDE and SATA drives offer far quicker performance, more like 50+ megs per second.

What is up with SATA in Ubuntu?? A Google search yields plenty of posts with the same complaint but not one with a solution!


Rev.

---

### Post by 3rdalbum on 2010-05-22
> **Rev2010 said:**
> Here's the line from my fstab that auto mounts my NTFS Windows drive:

/dev/sda1       /media/disk     ntfs-3g    defaults,umask=007,gid=46,noatime   0       0

When writing to the drive the max speed I get is 5 megabytes per second. 

NTFS-3G is implemented in user-space; most filesystem drivers are implemented in kernel space. This adds some CPU overheads; quite a bit of CPU overheads.

NTFS-3G also hasn't been optimised; the team behind it is focussing its energy on making it as stable and bug-free as possible before actually making it go faster. (I'd agree with this; what use is a fast filesystem driver if it's just going to damage the filesystem?)

In short, if you want faster transfers to NTFS, then you need a faster CPU. If you want to transfer big files to a Windows system, you should consider using an Ext filesystem driver on Windows, and mount your Linux partition from within Windows. It'll be faster.

---

### Post by Rev2010 on 2010-05-22
> **3rdalbum said:**
> In short, if you want faster transfers to NTFS, then you need a faster CPU.

Thanks for replying, but I've already noted it's not an NTFS thing as I've discovered the my SATA drives are ALL writing at ~5 megabytes per second, even the EXT3 formatted Linux drives.

This is a problem with SATA in Ubuntu. I've spent hours Googling this and there are hundreds of posts from others complaining about the exact same SATA slowness and not one thread has yielded an answer and I'm getting rather uptight about this. I have an Intel Q6600 quad core by the way. This problem is not occuring in my Windows XP boot, only in Ubuntu.

So, does anyone at all know how to get a SATA drive to perform at correct *write* speeds in Ubuntu?? Read is fine. This was of course never an issue with IDE drives.


Rev.

---

