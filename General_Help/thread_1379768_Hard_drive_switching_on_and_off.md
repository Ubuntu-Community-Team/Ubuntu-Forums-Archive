---
title: "Hard drive switching on and off"
date: 2010-01-12
forum: General Help
---

### Post by Aikon- on 2010-01-12
Recently I noticed my hard drive sounding like it was repeatedly clicking off and then immediately spinning back up. Obviously, this doesn't sound like it is very good for the hard drive, and may be the cause of my computer locking up the other night.

I believe the affected hard drive is a Seagate 1TB SATA drive I bought this past summer, which is connected to the on-board SATA controller (SiLabs, I think?). Here is the dmesg output from when the problem started occurring. Any suggestions on how to track down what's going on?

```

[ 1385.157814] ata1: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0xe frozen
[ 1385.157824] ata1: SError: { PHYRdyChg 10B8B }
[ 1385.157835] ata1: hard resetting link
[ 1389.300273] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1389.406471] ata1.00: configured for UDMA/100
[ 1389.406484] ata1: EH complete
[ 1389.946611] ata1: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0xe frozen
[ 1389.946621] ata1: SError: { PHYRdyChg 10B8B }
[ 1389.946632] ata1: hard resetting link
[ 1394.084055] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1394.190318] ata1.00: configured for UDMA/100
[ 1394.190330] ata1: EH complete
[ 1394.713263] ata1: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0xe frozen
[ 1394.713272] ata1: SError: { PHYRdyChg 10B8B }
[ 1394.713283] ata1: hard resetting link
[ 1398.684019] ata1: COMRESET failed (errno=-19)
[ 1398.684027] ata1: reset failed (errno=-19), retrying in 7 secs
[ 1404.712020] ata1: hard resetting link
[ 1405.436039] ata1: SATA link down (SStatus 0 SControl 310)
[ 1410.436051] ata1: hard resetting link
[ 1410.760086] ata1: SATA link down (SStatus 0 SControl 310)
[ 1415.760022] ata1: hard resetting link
[ 1416.080036] ata1: SATA link down (SStatus 0 SControl 310)
[ 1416.080053] ata1.00: disabled
[ 1416.080069] ata1: EH complete
[ 1416.080080] ata1.00: detaching (SCSI 0:0:0:0)
[ 1416.080920] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1416.080966] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 1416.080971] sd 0:0:0:0: [sda] Stopping disk
[ 1416.080983] sd 0:0:0:0: [sda] START_STOP FAILED
[ 1416.080985] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 1420.667688] ata1: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[ 1420.667697] ata1: SError: { PHYRdyChg }
[ 1420.667711] ata1: hard resetting link
[ 1422.136022] ata1: COMRESET failed (errno=-19)
[ 1422.136030] ata1: reset failed (errno=-19), retrying in 9 secs
[ 1430.664025] ata1: hard resetting link
[ 1431.388036] ata1: SATA link down (SStatus 0 SControl 310)
[ 1431.388056] ata1: EH complete
[ 1435.136452] ata1: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[ 1435.136461] ata1: SError: { PHYRdyChg }
[ 1435.136475] ata1: hard resetting link
[ 1440.868395] ata1: link is slow to respond, please be patient (ready=-19)
[ 1442.560340] ata1: COMRESET failed (errno=-19)
[ 1442.560348] ata1: reset failed (errno=-19), retrying in 3 secs
[ 1445.136030] ata1: hard resetting link
[ 1446.084025] ata1: COMRESET failed (errno=-19)
[ 1446.084033] ata1: reset failed (errno=-19), retrying in 10 secs
[ 1450.132429] metapage_write_end_io: I/O error
[ 1450.136285] metapage_write_end_io: I/O error
[ 1455.136022] ata1: hard resetting link
[ 1456.932031] ata1: COMRESET failed (errno=-19)
[ 1456.932040] ata1: reset failed (errno=-19), retrying in 34 secs
[ 1490.136027] ata1: hard resetting link
[ 1490.860036] ata1: SATA link down (SStatus 0 SControl 310)
[ 1490.860055] ata1: EH complete
[ 1504.264528] ata1: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[ 1504.264537] ata1: SError: { PHYRdyChg }
[ 1504.264551] ata1: hard resetting link
[ 1505.436021] ata1: COMRESET failed (errno=-19)
[ 1505.436029] ata1: reset failed (errno=-19), retrying in 9 secs
[ 1514.264023] ata1: hard resetting link
[ 1515.100022] ata1: COMRESET failed (errno=-19)
[ 1515.100030] ata1: reset failed (errno=-19), retrying in 10 secs
[ 1524.264020] ata1: hard resetting link
[ 1525.444028] ata1: COMRESET failed (errno=-19)
[ 1525.444036] ata1: reset failed (errno=-19), retrying in 34 secs
[ 1559.264021] ata1: hard resetting link
[ 1559.988034] ata1: SATA link down (SStatus 0 SControl 310)
[ 1559.988053] ata1: EH complete
[ 1560.278876] ata1: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[ 1560.278885] ata1: SError: { PHYRdyChg }
[ 1560.278899] ata1: hard resetting link
[ 1561.000050] ata1: SATA link down (SStatus 0 SControl 310)
[ 1561.000070] ata1: EH complete
[ 1569.408482] ata1: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[ 1569.408491] ata1: SError: { PHYRdyChg }
[ 1569.408505] ata1: hard resetting link
[ 1570.134913] ata1: SATA link down (SStatus 0 SControl 310)
[ 1570.134933] ata1: EH complete
[ 1571.171383] ata1: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[ 1571.171391] ata1: SError: { PHYRdyChg }
[ 1571.171406] ata1: hard resetting link
[ 1571.892037] ata1: SATA link down (SStatus 0 SControl 310)
[ 1571.892057] ata1: EH complete

```

It keeps on with that SATA link down, EH complete, etc.


-Aikon

---

### Post by iponeverything on 2010-01-12
This looks to me like a bad drive. Try checking your cables and connections. See if has the same issue with a different version of ubuntu on live CD. If you can't find the cause as not being an issue with the HD itself, I would back it up if has important data add see if I could RMA it.

---

### Post by Aikon- on 2010-01-16
Seems to be the cable; as long as I am conscious when I finish messing around in my computer, I can prevent it be ensuring the connectors are firmly inserted.

I miss the rigidity of PATA connectors =/

-Aikon

---

