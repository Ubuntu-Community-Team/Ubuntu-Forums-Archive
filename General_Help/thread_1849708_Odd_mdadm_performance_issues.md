---
title: "Odd mdadm performance issues"
date: 2011-09-25
forum: General Help
---

### Post by pentas on 2011-09-25
Just finished rebuilding my file server after what I thought was a failed RAID card.  Just to be sure, the machine's got a different motherboard (onboard SATA) and a different SATA card.  For what it's worth, the machine has 9x 500GB drives.  All are Seagate, 7200RPM, and are either 7200.10 (3x) or 7200.11 (6x).

With hdparm, I can test each drive individually.  All drives respond well and report speeds anywhere from 70 MB/s to 110 MB/s, depending on the drive.  The external SATA card does not seem to have any effect on drive speed.

The issue is the overall performance of the array.  I have it setup as a RAID6 array, but resync performance tops out at ~13 MB/s, and drops to 4 MB/s if I simultaneously format the array while it's resyncing. Previously, I could only move data to and from the array at a maximum speed of 4.5 MB/s.

Anyone have any idea what might be going on?  The machine is pretty much idling (~10% CPU usage, 93% free memory).  It's got me stumped...

---

### Post by dcstar on 2011-09-25
> **pentas said:**
> Just finished rebuilding my file server after what I thought was a failed RAID card.  Just to be sure, the machine's got a different motherboard (onboard SATA) and a different SATA card.  For what it's worth, the machine has 9x 500GB drives.  All are Seagate, 7200RPM, and are either 7200.10 (3x) or 7200.11 (6x).

With hdparm, I can test each drive individually.  All drives respond well and report speeds anywhere from 70 MB/s to 110 MB/s, depending on the drive.  The external SATA card does not seem to have any effect on drive speed.

The issue is the overall performance of the array.  I have it setup as a RAID6 array, but resync performance tops out at ~13 MB/s, and drops to 4 MB/s if I simultaneously format the array while it's resyncing. Previously, I could only move data to and from the array at a maximum speed of 4.5 MB/s.

Anyone have any idea what might be going on?  The machine is pretty much idling (~10% CPU usage, 93% free memory).  It's got me stumped...

Since it's different hardware then there could be a multitude of reasons. Also since we have NO IDEA of what version of Ubuntu you are using it also makes things difficult.

---

### Post by pentas on 2011-09-25
> **dcstar said:**
> Since it's different hardware then there could be a multitude of reasons. Also since we have NO IDEA of what version of Ubuntu you are using it also makes things difficult.

The problem exists with 10.04 LTS, but also exists with Debian Squeeze stable and CentOS 6.

---

