---
title: "general slowness when manipulating large files"
date: 2010-11-04
forum: General Help
---

### Post by sotanez on 2010-11-04
Hi.
This is an issue that have happened to me in all the releases of Kubuntu that I have installed.
When copying, unzipping, etc. large files the system gets so slow that I have to wait until the action finishes. It is like the system does not schedule well the access to the hard drive and just let the process have all the hard drive at its will.
This issue does not happen in Windows XP: for instance, it lets me start Firefox in reasonable time while extracting or copying a large file.
I know there are commands like ionice to control this, but I would like to know if there is some general policy I could set to control all the processes that access to my hard drive. Or maybe you could tell me if this only happens to me.

Right now I am using Kubuntu 10.04 64 bits

This is the output for hdparm -tT /dev/sda

```
/dev/sda:
 Timing cached reads:   1416 MB in  2.00 seconds = 707.70 MB/sec
 Timing buffered disk reads:  162 MB in  3.01 seconds =  53.83 MB/sec

```

This is the output for sdparm -all /dev/sda

```
    /dev/sda: ATA       WDC WD2500JD-40H  21.0
    Direct access device specific parameters: WP=0  DPOFUA=0
Read write error recovery [rw] mode page [PS=0]:
  AWRE        1  Automatic write reallocation enabled
  ARRE        0  Automatic read reallocation enabled
  TB          0  Transfer block
  RC          0  Read continuous
        0: error recovery may cause delays
        1: transfer data without waiting for error recovery
  EER         0  Enable early recovery
  PER         0  Post error
        0: do not post recovered errors
        1: report recovered errors
  DTE         0  Data terminate on error
  DCR         0  Disable correction
  RRC         0  Read retry count
  COR_S       0  Correction span (obsolete)
  HOC         0  Head offset count (obsolete)
  DSOC        0  Data strobe offset count (obsolete)
  WRC         0  Write retry count
  RTL         0  Recovery time limit (ms)
Caching (SBC) [ca] mode page [PS=0]:
  IC          0  Initiator control
        0: disk uses own adaptive caching algorithm
        1: disk caching algorithm controlled by NCS or CCS
  ABPF        0  Abort pre-fetch
  CAP         0  Caching analysis permitted
  DISC        0  Discontinuity
        0: pre-fetch truncated or wrapped at time discontinuity
        1: pre-fetch continues across time discontinuity
  SIZE        0  Size enable
        0: number of cache segments (NCS) controls cache segmentation
        1: the cache segment size (CCS) controls cache segmentation
  WCE         1  Write cache enable
  MF          0  Multiplication factor
        0: MIPF and MAPF specify blocks
        1: multiply MIPF and MAPF by blocks in read command
  RCD         0  Read cache disable
  DRRP        0  Demand read retention priority
        0: treat requested and other data equally
        1: replace requested data before other data
        15: replace other data before requested data
  WRP         0  Write retention priority
        0: treat requested and other data equally
        1: replace requested data before other data
        15: replace other data before requested data
  DPTL        0  Disable pre-fetch transfer length
  MIPF        0  Minimum pre-fetch
  MAPF        0  Maximum pre-fetch
  MAPFC       0  Maximum pre-fetch ceiling
  FSW         0  Force sequential write
  LBCSS       0  Logical block cache segment size
        0: CSS unit is bytes; 1: CSS unit is blocks
  DRA         0  Disable read ahead
  NV_DIS      0  Non-volatile cache disable
  NCS         0  Number of cache segments
  CSS         0  Cache segment size
Control [co] mode page [PS=0]:
  TST         0  Task set type
        0: lu maintains one task set for all I_T nexuses
        1: lu maintains separate task sets for each I_T nexus
  TMF_ONLY    0  Task management functions only
  D_SENSE     0  Descriptor format sense data
  GLTSD       1  Global logging target save disable
  RLEC        0  Report log exception condition
  QAM         0  Queue algorithm modifier
        0: restricted re-ordering; 1: unrestricted
  QERR        0  Queue error management
        0: only affected task gets CC; 1: affected tasks aborted
        3: affected tasks aborted on same I_T nexus
  RAC         0  Report a check
  UA_INTLCK   0  Unit attention interlocks control
        0: unit attention cleared with check condition status
        2: unit attention not cleared with check condition status
        3: as 2 plus ua on busy, task set full or reservation conflict
  SWP         0  Software write protect
  ATO         0  Application tag owner
  TAS         0  Task aborted status
        0: tasks aborted without response to app client
        1: any other I_T nexuses receive task aborted
  AUTOLOAD    0  Autoload mode
        0: medium loaded for full access
        1: loaded for medium auxiliary access only
        2: medium shall not be loaded
  BTP        -1  Busy timeout period (100us)
  ESTCT      30  Extended self test completion time (sec)

```

---

### Post by dcstar on 2010-11-05
> **sotanez said:**
> Hi.
This is an issue that have happened to me in all the releases of Kubuntu that I have installed.
When copying, unzipping, etc. large files the system gets so slow that I have to wait until the action finishes. It is like the system does not schedule well the access to the hard drive and just let the process have all the hard drive at its will.
.........

Experiment with different schedulers in the boot string:

[http://ubuntuforums.org/showthread.php?t=119546](http://ubuntuforums.org/showthread.php?t=119546)

---

