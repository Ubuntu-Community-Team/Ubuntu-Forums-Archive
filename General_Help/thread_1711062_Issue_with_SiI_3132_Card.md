---
title: "Issue with SiI 3132 Card"
date: 2011-03-20
forum: General Help
---

### Post by Bountin on 2011-03-20
Hi,

I'm trying to use a SiI 3132 Card - Two 2TB harddrives are attached to it. If I run badblocks over one of them, it crashes at about 1/3 and the harddrives are unuseable (until the next reboot)

dmesg is ful of the following:
[16243.478235] end_request: I/O error, dev sdb, sector 1624313160
[16243.478724] sd 2:0:1:0: [sdb] Unhandled error code
[16243.478727] sd 2:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[16243.478731] sd 2:0:1:0: [sdb] CDB: Read(10): 28 00 60 d1 0d 48 00 00 08 00
[16243.478741] end_request: I/O error, dev sdb, sector 1624313160
[16243.479286] sd 2:0:1:0: [sdb] Unhandled error code
[16243.479289] sd 2:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[16243.479293] sd 2:0:1:0: [sdb] CDB: Read(10): 28 00 60 d1 0d 48 00 00 08 00
[16243.479302] end_request: I/O error, dev sdb, sector 1624313160

Any idea how I can fix this or how I can investigate this issue further? 

The harddrives are okay, they work as expected with the board's sata ports.

---

### Post by tobiz on 2011-07-20
Did you ever get the SiL 3132 card to work ok?

---

