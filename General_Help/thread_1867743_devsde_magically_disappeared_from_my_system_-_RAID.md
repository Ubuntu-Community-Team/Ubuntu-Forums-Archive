---
title: "/dev/sde magically disappeared from my system - RAID6 mdadm ubuntu 11.10"
date: 2011-10-23
forum: General Help
---

### Post by alfonso78 on 2011-10-23
Hi there,

I got an email from mdadm:

```
This is an automatically generated mail message from mdadm
running on NAS

A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sde1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid6 sdb1[2] sdd1[0] sde1[4](F) sda1[3]
     3907023872 blocks level 6, 64k chunk, algorithm 2 [4/3] [U_UU]

unused devices: <none>

```

In the box, I checked syslog:

```
Oct 23 15:41:10 NAS kernel: [56484.867853] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 15:41:10 NAS kernel: [56484.867859] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 15:41:10 NAS kernel: [56484.867869] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 00 fe ab 2f 00 00 08 00
Oct 23 15:41:10 NAS kernel: [56484.867878] end_request: I/O error, dev sde, sector 16689967
Oct 23 15:41:10 NAS kernel: [56484.867894] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 15:41:10 NAS kernel: [56484.867897] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 15:41:10 NAS kernel: [56484.867899] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 01 5a 26 67 00 00 28 00
Oct 23 15:41:10 NAS kernel: [56484.867907] end_request: I/O error, dev sde, sector 22685287
Oct 23 15:41:10 NAS kernel: [56484.867920] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 15:41:10 NAS kernel: [56484.867922] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 15:41:10 NAS kernel: [56484.867925] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 9c 66 b2 af 00 00 90 00
Oct 23 15:41:10 NAS kernel: [56484.867932] end_request: I/O error, dev sde, sector 2623976111
Oct 23 15:41:10 NAS kernel: [56484.867943] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 15:41:10 NAS kernel: [56484.867945] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 15:41:10 NAS kernel: [56484.867947] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 9c 66 b4 3f 00 00 70 00
Oct 23 15:41:10 NAS kernel: [56484.867954] end_request: I/O error, dev sde, sector 2623976511
Oct 23 15:41:10 NAS kernel: [56484.867975] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 15:41:10 NAS kernel: [56484.867978] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 15:41:10 NAS kernel: [56484.867980] sd 3:0:0:0: [sde] CDB: Write(10): 2a 00 e8 e0 74 3f 00 00 08 00
Oct 23 15:41:10 NAS kernel: [56484.867988] end_request: I/O error, dev sde, sector 3907023935
Oct 23 15:41:10 NAS kernel: [56484.867991] end_request: I/O error, dev sde, sector 3907023935
Oct 23 15:41:10 NAS kernel: [56484.867998] md/raid:md0: Disk failure on sde1, disabling device.
Oct 23 15:41:10 NAS kernel: [56484.868015] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 15:41:10 NAS kernel: [56484.868017] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 15:41:10 NAS kernel: [56484.868020] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 00 da b7 27 00 00 08 00
Oct 23 15:41:10 NAS kernel: [56484.868029] end_request: I/O error, dev sde, sector 14333735
Oct 23 15:41:11 NAS kernel: [56485.956677]  disk 1, o:0, dev:sde1
Oct 23 15:41:11 NAS mdadm[1577]: Fail event detected on md device /dev/md0, component device /dev/sde1

```

I tried to manually recover the array:

```
sudo mdadm --remove /dev/md0 /dev/sde1
```

and then re-add the device

```
sudo mdadm --add /dev/md0 /dev/sde1
```

And the output is:

```
mdadm: failed to write superblock to /dev/sde1
```

So I tried this:

```
sudo fdisk -l /dev/sde
```

and syslog says:

```
Oct 23 16:45:07 NAS kernel: [60319.110057] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 16:45:07 NAS kernel: [60319.110063] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:45:07 NAS kernel: [60319.110069] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
Oct 23 16:45:07 NAS kernel: [60319.110083] end_request: I/O error, dev sde, sector 0
Oct 23 16:45:07 NAS kernel: [60319.110088] quiet_error: 1 callbacks suppressed
Oct 23 16:45:07 NAS kernel: [60319.110092] Buffer I/O error on device sde, logical block 0
Oct 23 16:45:07 NAS kernel: [60319.110098] Buffer I/O error on device sde, logical block 1
Oct 23 16:45:07 NAS kernel: [60319.110104] Buffer I/O error on device sde, logical block 2
Oct 23 16:45:07 NAS kernel: [60319.110109] Buffer I/O error on device sde, logical block 3
Oct 23 16:45:07 NAS kernel: [60319.110131] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 16:45:07 NAS kernel: [60319.110136] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:45:07 NAS kernel: [60319.110157] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Oct 23 16:45:07 NAS kernel: [60319.110169] end_request: I/O error, dev sde, sector 0
Oct 23 16:45:07 NAS kernel: [60319.110173] Buffer I/O error on device sde, logical block 0
Oct 23 16:45:07 NAS kernel: [60319.110246] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 16:45:07 NAS kernel: [60319.110250] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:45:07 NAS kernel: [60319.110255] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 e8 e0 88 a8 00 00 08 00
Oct 23 16:45:07 NAS kernel: [60319.110267] end_request: I/O error, dev sde, sector 3907029160
Oct 23 16:45:07 NAS kernel: [60319.110271] Buffer I/O error on device sde, logical block 488378645
Oct 23 16:45:07 NAS kernel: [60319.110332] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 16:45:07 NAS kernel: [60319.110336] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:45:07 NAS kernel: [60319.110341] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 e8 e0 88 a8 00 00 08 00
Oct 23 16:45:07 NAS kernel: [60319.110353] end_request: I/O error, dev sde, sector 3907029160
Oct 23 16:45:07 NAS kernel: [60319.110357] Buffer I/O error on device sde, logical block 488378645
Oct 23 16:45:07 NAS kernel: [60319.110454] sd 3:0:0:0: [sde] Unhandled error code
Oct 23 16:45:07 NAS kernel: [60319.110458] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:45:07 NAS kernel: [60319.110463] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Oct 23 16:45:07 NAS kernel: [60319.110475] end_request: I/O error, dev sde, sector 0
Oct 23 16:45:07 NAS kernel: [60319.110479] Buffer I/O error on device sde, logical block 0

```

At the same time I get these errors in syslog (which I think are related):

```
Oct 23 16:40:59 NAS kernel: [60071.665484] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 23 16:40:59 NAS kernel: [60071.665492] ata3.00: failed command: FLUSH CACHE EXT
Oct 23 16:40:59 NAS kernel: [60071.665502] ata3.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct 23 16:40:59 NAS kernel: [60071.665504]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Oct 23 16:40:59 NAS kernel: [60071.665509] ata3.00: status: { DRDY }
Oct 23 16:40:59 NAS kernel: [60071.665519] ata3: hard resetting link
Oct 23 16:41:05 NAS kernel: [60077.178096] ata3: link is slow to respond, please be patient (ready=0)
Oct 23 16:41:09 NAS kernel: [60081.711287] ata3: SRST failed (errno=-16)
Oct 23 16:41:09 NAS kernel: [60081.711301] ata3: hard resetting link
Oct 23 16:41:15 NAS kernel: [60087.223922] ata3: link is slow to respond, please be patient (ready=0)
Oct 23 16:41:19 NAS kernel: [60091.757093] ata3: SRST failed (errno=-16)
Oct 23 16:41:19 NAS kernel: [60091.757106] ata3: hard resetting link
Oct 23 16:41:25 NAS kernel: [60097.269730] ata3: link is slow to respond, please be patient (ready=0)
Oct 23 16:41:30 NAS udevd[32690]: timeout '/sbin/mdadm --detail --export /dev/md0'
Oct 23 16:41:31 NAS udevd[32690]: timeout: killing '/sbin/mdadm --detail --export /dev/md0' [4054]
Oct 23 16:41:54  udevd[32690]: last message repeated 23 times
Oct 23 16:41:54 NAS kernel: [60126.763594] ata3: SRST failed (errno=-16)
Oct 23 16:41:54 NAS kernel: [60126.763604] ata3: limiting SATA link speed to 1.5 Gbps
Oct 23 16:41:54 NAS kernel: [60126.763612] ata3: hard resetting link
Oct 23 16:41:55 NAS udevd[32690]: timeout: killing '/sbin/mdadm --detail --export /dev/md0' [4054]
Oct 23 16:41:59  udevd[32690]: last message repeated 4 times
Oct 23 16:41:59 NAS udevd[32690]: '/sbin/mdadm --detail --export /dev/md0' [4054] terminated by signal 9 (Killed)
Oct 23 16:41:59 NAS udevd[32690]: timeout '/sbin/blkid -o udev -p /dev/md0'
Oct 23 16:41:59 NAS kernel: [60131.772489] ata3: SRST failed (errno=-16)
Oct 23 16:41:59 NAS kernel: [60131.772498] ata3: reset failed, giving up
Oct 23 16:41:59 NAS kernel: [60131.772504] ata3.00: disabled
Oct 23 16:41:59 NAS kernel: [60131.772511] ata3.00: device reported invalid CHS sector 0
Oct 23 16:41:59 NAS kernel: [60131.772525] ata3: EH complete
Oct 23 16:41:59 NAS kernel: [60131.772614] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772617] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772622] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 00 ef 91 97 00 01 60 00
Oct 23 16:41:59 NAS kernel: [60131.772631] end_request: I/O error, dev sdd, sector 15700375
Oct 23 16:41:59 NAS kernel: [60131.772673] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772674] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772677] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 00 ef 92 f7 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.772682] end_request: I/O error, dev sdd, sector 15700727
Oct 23 16:41:59 NAS kernel: [60131.772698] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772699] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772701] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 02 18 ac 3f 00 00 10 00
Oct 23 16:41:59 NAS kernel: [60131.772707] end_request: I/O error, dev sdd, sector 35171391
Oct 23 16:41:59 NAS kernel: [60131.772715] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772716] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772718] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 02 71 22 c7 00 00 78 00
Oct 23 16:41:59 NAS kernel: [60131.772724] end_request: I/O error, dev sdd, sector 40968903
Oct 23 16:41:59 NAS kernel: [60131.772747] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772748] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772750] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 02 71 23 3f 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.772755] end_request: I/O error, dev sdd, sector 40969023
Oct 23 16:41:59 NAS kernel: [60131.772767] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772769] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772771] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 02 71 24 3f 00 00 88 00
Oct 23 16:41:59 NAS kernel: [60131.772776] end_request: I/O error, dev sdd, sector 40969279
Oct 23 16:41:59 NAS kernel: [60131.772804] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772806] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772808] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 02 71 24 bf 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.772813] end_request: I/O error, dev sdd, sector 40969407
Oct 23 16:41:59 NAS kernel: [60131.772824] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772826] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772828] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 03 c2 7e 3f 00 00 88 00
Oct 23 16:41:59 NAS kernel: [60131.772834] end_request: I/O error, dev sdd, sector 63077951
Oct 23 16:41:59 NAS kernel: [60131.772850] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772852] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772854] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 03 c2 7e bf 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.772860] end_request: I/O error, dev sdd, sector 63078079
Oct 23 16:41:59 NAS kernel: [60131.772872] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772874] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772876] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 03 c5 8d 3f 00 00 10 00
Oct 23 16:41:59 NAS kernel: [60131.772882] end_request: I/O error, dev sdd, sector 63278399
Oct 23 16:41:59 NAS kernel: [60131.772890] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772892] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772894] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 03 c5 8e 3f 00 00 30 00
Oct 23 16:41:59 NAS kernel: [60131.772900] end_request: I/O error, dev sdd, sector 63278655
Oct 23 16:41:59 NAS kernel: [60131.772921] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772922] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772924] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 8b a4 69 3f 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.772930] end_request: I/O error, dev sdd, sector 2342807871
Oct 23 16:41:59 NAS kernel: [60131.772943] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772944] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772947] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 8b a4 6a 3f 00 01 00 00
Oct 23 16:41:59 NAS kernel: [60131.772953] end_request: I/O error, dev sdd, sector 2342808127
Oct 23 16:41:59 NAS kernel: [60131.772985] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.772987] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.772989] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 8b a4 6a bf 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.772996] end_request: I/O error, dev sdd, sector 2342808255
Oct 23 16:41:59 NAS kernel: [60131.773025] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.773027] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.773029] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 de 60 09 67 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.773036] end_request: I/O error, dev sdd, sector 3730835815
Oct 23 16:41:59 NAS kernel: [60131.773043] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.773045] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.773048] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 de 60 09 7f 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.773054] end_request: I/O error, dev sdd, sector 3730835839
Oct 23 16:41:59 NAS kernel: [60131.773061] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.773062] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.773065] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 de 60 09 b7 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.773072] end_request: I/O error, dev sdd, sector 3730835895
Oct 23 16:41:59 NAS kernel: [60131.773146] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.773148] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.773151] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 de 60 89 67 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.773157] end_request: I/O error, dev sdd, sector 3730868583
Oct 23 16:41:59 NAS kernel: [60131.773166] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.773168] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.773170] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 e8 e0 74 3f 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.773176] end_request: I/O error, dev sdd, sector 3907023935
Oct 23 16:41:59 NAS kernel: [60131.775609] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775613] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775616] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 00 ef 91 97 00 01 60 00
Oct 23 16:41:59 NAS kernel: [60131.775622] end_request: I/O error, dev sdd, sector 15700375
Oct 23 16:41:59 NAS kernel: [60131.775626] md/raid:md0: Disk failure on sdd1, disabling device.
Oct 23 16:41:59 NAS kernel: [60131.775626] md/raid:md0: Operation continuing on 2 devices.
Oct 23 16:41:59 NAS kernel: [60131.775645] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775647] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775650] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 02 18 ac 3f 00 00 10 00
Oct 23 16:41:59 NAS kernel: [60131.775656] end_request: I/O error, dev sdd, sector 35171391
Oct 23 16:41:59 NAS kernel: [60131.775664] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775665] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775667] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 02 71 22 c7 00 00 78 00
Oct 23 16:41:59 NAS kernel: [60131.775672] end_request: I/O error, dev sdd, sector 40968903
Oct 23 16:41:59 NAS kernel: [60131.775679] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775680] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775682] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 02 71 24 3f 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.775686] end_request: I/O error, dev sdd, sector 40969279
Oct 23 16:41:59 NAS kernel: [60131.775692] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775693] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775695] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 02 71 24 bf 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.775700] end_request: I/O error, dev sdd, sector 40969407
Oct 23 16:41:59 NAS kernel: [60131.775704] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775706] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775707] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 03 c2 7e 3f 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.775712] end_request: I/O error, dev sdd, sector 63077951
Oct 23 16:41:59 NAS kernel: [60131.775718] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775719] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775721] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 03 c2 7e bf 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.775725] end_request: I/O error, dev sdd, sector 63078079
Oct 23 16:41:59 NAS kernel: [60131.775730] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775731] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775733] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 03 c5 8e 3f 00 00 30 00
Oct 23 16:41:59 NAS kernel: [60131.775737] end_request: I/O error, dev sdd, sector 63278655
Oct 23 16:41:59 NAS kernel: [60131.775742] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775743] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775745] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 8b a4 6a 3f 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.775750] end_request: I/O error, dev sdd, sector 2342808127
Oct 23 16:41:59 NAS kernel: [60131.775756] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775758] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775759] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 8b a4 6a bf 00 00 80 00
Oct 23 16:41:59 NAS kernel: [60131.775764] end_request: I/O error, dev sdd, sector 2342808255
Oct 23 16:41:59 NAS kernel: [60131.775770] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775771] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775773] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 de 60 09 67 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.775777] end_request: I/O error, dev sdd, sector 3730835815
Oct 23 16:41:59 NAS kernel: [60131.775781] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775782] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775784] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 de 60 09 7f 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.775789] end_request: I/O error, dev sdd, sector 3730835839
Oct 23 16:41:59 NAS kernel: [60131.775793] sd 2:0:0:0: [sdd] Unhandled error code
Oct 23 16:41:59 NAS kernel: [60131.775794] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 16:41:59 NAS kernel: [60131.775796] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 de 60 09 b7 00 00 08 00
Oct 23 16:41:59 NAS kernel: [60131.775800] end_request: I/O error, dev sdd, sector 3730835895
Oct 23 16:42:00 NAS kernel: [60132.064399] RAID conf printout:
Oct 23 16:42:00 NAS kernel: [60132.064406]  --- level:6 rd:4 wd:2
Oct 23 16:42:00 NAS kernel: [60132.064410]  disk 0, o:0, dev:sdd1
Oct 23 16:42:00 NAS kernel: [60132.064414]  disk 2, o:1, dev:sdb1
Oct 23 16:42:00 NAS kernel: [60132.064417]  disk 3, o:1, dev:sda1
Oct 23 16:42:00 NAS udevd[32690]: timeout 'udisks-part-id /dev/md0'
Oct 23 16:42:00 NAS kernel: [60132.072336] RAID conf printout:
Oct 23 16:42:00 NAS kernel: [60132.072343]  --- level:6 rd:4 wd:2
Oct 23 16:42:00 NAS kernel: [60132.072348]  disk 2, o:1, dev:sdb1
Oct 23 16:42:00 NAS kernel: [60132.072351]  disk 3, o:1, dev:sda1
Oct 23 16:42:00 NAS mdadm[1577]: Fail event detected on md device /dev/md0, component device /dev/sdd1
Oct 23 16:42:00 NAS postfix/pickup[2764]: 596C418044C: uid=0 from=<root>
Oct 23 16:42:00 NAS postfix/cleanup[4081]: 596C418044C: message-id=<20111023144200.596C418044C@NAS>
Oct 23 16:42:00 NAS postfix/qmgr[3147]: 596C418044C: from=<root@NAS>, size=811, nrcpt=1 (queue active)
Oct 23 16:42:05 NAS postfix/smtp[4083]: 596C418044C: to=<my.name@gmail.com>, relay=smtp.gmail.com[209.85.229.109]:587, delay=5.3, delays=0.36/0.26/2.7/2, dsn=2.0.0, status=sent (250 2.0.0 OK 1319380915 fi11sm33445001wbb.9)
Oct 23 16:42:05 NAS postfix/qmgr[3147]: 596C418044C: removed

```

**[COLOR="Red"]WOW!!! An other device failed!!! :( :([/COLOR]**

My MB is a Zotac H55 ( [http://www.zotac.com/index.php?option=com_virtuemart&Itemid=100194&lang=un&vmcchk=1&Itemid=100194](http://www.zotac.com/index.php?option=com_virtuemart&Itemid=100194&lang=un&vmcchk=1&Itemid=100194) ) and I run Ubuntu 11.10

Ok, now I'm in panic mode.

I'll reboot the machine and try to add the two disks again.

what's going on????

---

### Post by alfonso78 on 2011-10-23
I tried to reboot and ubuntu does not see the two drives anymore.

I tried to shutdown and restart, same result.

I checked, and the BIOS can still see these two HDs that ubuntu does not see them anymore.


:confused:

---

### Post by alfonso78 on 2011-10-23
I'm really really puzzled!

Booting from a bootable ubuntu 11.10 USB key, I can see all 4 disks plus the OS disk.

and now rebooting in the main system, I can see all four disks.

```
$ sudo mdadm --add /dev/md0 /dev/sdd1
mdadm: added /dev/sdd1
$ sudo mdadm --add /dev/md0 /dev/sde1
mdadm: added /dev/sde1

```

```
$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid6 sde1[4](S) sdd1[5] sdb1[2] sda1[3]
      3907023872 blocks level 6, 64k chunk, algorithm 2 [4/2] [__UU]
      [>....................]  recovery =  0.0% (1777528/1953511936) finish=475.7min speed=68366K/sec

unused devices: <none>

```

at the time of this failure, I was doing a disk intensive task:

md5sum of all files on the disk.

I won't restart that until the RAID is in sync and I will buy SATA cable (I've read the standard ones are quite low quality).

**Does anyone have any idea of a non-destructive test I could carry out to verify if the disks have problems?**

Thank you.

---

### Post by alfonso78 on 2011-10-23
the raid was being rebuilt and there was no heavy CPU task ongoing.

**[COLOR="Red"]Finally one more disk failed and the whole RAID is lost:[/COLOR]**

```
**Fail event on /dev/md0:NAS**

This is an automatically generated mail message from mdadm
running on NAS

A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sda1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid6 sde1[4](S) sdd1[5] sdb1[2] sda1[6](F)
     3907023872 blocks level 6, 64k chunk, algorithm 2 [4/1] [__U_]

unused devices: <none>
```

Where should I start looking for a problem?

What test can I do?

It seems impossible to me that 3 disks all new fail all in the same day...

any idea?

---

### Post by alfonso78 on 2011-10-23
This is what syslog said:

```
Oct 23 23:51:18 NAS kernel: [23180.786485] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 frozen
Oct 23 23:51:18 NAS kernel: [23180.786492] ata1.01: failed command: FLUSH CACHE EXT
Oct 23 23:51:18 NAS kernel: [23180.786500] ata1.01: cmd ea/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Oct 23 23:51:18 NAS kernel: [23180.786501]          res 40/00:00:00:4f:c2/00:00:00:00:00/50 Emask 0x4 (timeout)
Oct 23 23:51:18 NAS kernel: [23180.786505] ata1.01: status: { DRDY }
Oct 23 23:51:18 NAS kernel: [23180.786514] ata1.00: hard resetting link
Oct 23 23:51:19 NAS kernel: [23181.106290] ata1.01: hard resetting link
Oct 23 23:51:24 NAS kernel: [23186.618864] ata1.00: link is slow to respond, please be patient (ready=-19)
Oct 23 23:51:28 NAS kernel: [23190.816317] ata1.00: SRST failed (errno=-16)
Oct 23 23:51:28 NAS kernel: [23190.816328] ata1.00: hard resetting link
Oct 23 23:51:29 NAS kernel: [23191.136109] ata1.01: hard resetting link
Oct 23 23:51:34 NAS kernel: [23196.648743] ata1.00: link is slow to respond, please be patient (ready=-19)
Oct 23 23:51:38 NAS kernel: [23200.846144] ata1.00: SRST failed (errno=-16)
Oct 23 23:51:38 NAS kernel: [23200.846155] ata1.00: hard resetting link
Oct 23 23:51:39 NAS kernel: [23201.165949] ata1.01: hard resetting link
Oct 23 23:51:44 NAS kernel: [23206.678543] ata1.00: link is slow to respond, please be patient (ready=-19)
Oct 23 23:52:13 NAS kernel: [23235.836609] ata1.00: SRST failed (errno=-16)
Oct 23 23:52:13 NAS kernel: [23235.836619] ata1.00: limiting SATA link speed to 1.5 Gbps
Oct 23 23:52:13 NAS kernel: [23235.836624] ata1.01: limiting SATA link speed to 1.5 Gbps
Oct 23 23:52:13 NAS kernel: [23235.836631] ata1.00: hard resetting link
Oct 23 23:52:14 NAS kernel: [23236.156423] ata1.01: hard resetting link
Oct 23 23:52:18 NAS kernel: [23240.885505] ata1.00: SRST failed (errno=-16)
Oct 23 23:52:18 NAS kernel: [23240.885511] ata1.00: reset failed, giving up
Oct 23 23:52:18 NAS kernel: [23240.885516] ata1.01: disabled
Oct 23 23:52:18 NAS kernel: [23240.885522] ata1.01: device reported invalid CHS sector 0
Oct 23 23:52:18 NAS kernel: [23240.885533] ata1: EH complete
Oct 23 23:52:18 NAS kernel: [23240.885599] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.885604] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.885610] sd 0:0:1:0: [sda] CDB: Write(10): 2a 00 e8 e0 74 3f 00 00 08 00
Oct 23 23:52:18 NAS kernel: [23240.885624] end_request: I/O error, dev sda, sector 3907023935
Oct 23 23:52:18 NAS kernel: [23240.885629] end_request: I/O error, dev sda, sector 3907023935
Oct 23 23:52:18 NAS kernel: [23240.885633] md: super_written gets error=-5, uptodate=0
Oct 23 23:52:18 NAS kernel: [23240.885639] md/raid:md0: Disk failure on sda1, disabling device.
Oct 23 23:52:18 NAS kernel: [23240.885641] md/raid:md0: Operation continuing on 1 devices.
Oct 23 23:52:18 NAS kernel: [23240.885697] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.885702] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.885709] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 da 47 36 c7 00 00 f8 00
Oct 23 23:52:18 NAS kernel: [23240.885725] end_request: I/O error, dev sda, sector 3662100167
Oct 23 23:52:18 NAS kernel: [23240.885733] md/raid:md0: read error not correctable (sector 3662100104 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885739] md/raid:md0: read error not correctable (sector 3662100112 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885745] md/raid:md0: read error not correctable (sector 3662100120 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885751] md/raid:md0: read error not correctable (sector 3662100128 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885756] md/raid:md0: read error not correctable (sector 3662100136 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885762] md/raid:md0: read error not correctable (sector 3662100144 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885768] md/raid:md0: read error not correctable (sector 3662100152 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885773] md/raid:md0: read error not correctable (sector 3662100160 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885779] md/raid:md0: read error not correctable (sector 3662100168 on sda1).
Oct 23 23:52:18 NAS kernel: [23240.885828] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.885832] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.885838] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 da 47 38 3f 00 01 00 00
Oct 23 23:52:18 NAS kernel: [23240.885854] end_request: I/O error, dev sda, sector 3662100543
Oct 23 23:52:18 NAS kernel: [23240.885938] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.885941] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.885946] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 00 82 b2 ef 00 00 50 00
Oct 23 23:52:18 NAS kernel: [23240.885958] end_request: I/O error, dev sda, sector 8565487
Oct 23 23:52:18 NAS kernel: [23240.885994] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.885998] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.886002] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 af 75 8c 3f 00 04 00 00
Oct 23 23:52:18 NAS kernel: [23240.886014] end_request: I/O error, dev sda, sector 2943716415
Oct 23 23:52:18 NAS kernel: [23240.886264] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.886268] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.886273] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 af 75 90 3f 00 01 b0 00
Oct 23 23:52:18 NAS kernel: [23240.886285] end_request: I/O error, dev sda, sector 2943717439
Oct 23 23:52:18 NAS kernel: [23240.893482] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.893487] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.893492] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 de 60 89 4f 00 00 08 00
Oct 23 23:52:18 NAS kernel: [23240.893505] end_request: I/O error, dev sda, sector 3730868559
Oct 23 23:52:18 NAS kernel: [23240.901558] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.901564] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.901569] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 da 47 37 3f 00 01 00 00
Oct 23 23:52:18 NAS kernel: [23240.901583] end_request: I/O error, dev sda, sector 3662100287
Oct 23 23:52:18 NAS kernel: [23240.901601] sd 0:0:1:0: [sda] Unhandled error code
Oct 23 23:52:18 NAS kernel: [23240.901605] sd 0:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 23 23:52:18 NAS kernel: [23240.901610] sd 0:0:1:0: [sda] CDB: Read(10): 28 00 00 82 b3 3f 00 00 30 00
Oct 23 23:52:18 NAS kernel: [23240.901622] end_request: I/O error, dev sda, sector 8565567
Oct 23 23:52:18 NAS kernel: [23240.921455] md: md0: recovery done.
Oct 23 23:52:19 NAS mdadm[1621]: Fail event detected on md device /dev/md0, component device /dev/sda1

```

And these are the details of one of the four disks. The four disks are all the same:

```
$ sudo smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-12-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD1RNB9
LU WWN Device Id: 5 000c50 02f86852b
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Oct 24 00:22:52 2011 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (  623) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       101428200
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       71
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   074   060   030    Pre-fail  Always       -       25492150
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       379
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       71
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   097   097   000    Old_age   Always       -       3
190 Airflow_Temperature_Cel 0x0022   069   066   045    Old_age   Always       -       31 (Min/Max 31/33)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       47
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       71
194 Temperature_Celsius     0x0022   031   040   000    Old_age   Always       -       31 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   035   011   000    Old_age   Always       -       101428200
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       157075543949692
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3214257849
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1507340087

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

and attached the output of report-hw

---

### Post by alfonso78 on 2011-10-24
the only idea I got so far is check if heat is the root cause.

So I opened the case and now I'm running 

```
sudo badblocks -v /dev/sdd
```

My guess is that disks are fine and the problem might be heat or maybe faulty SATA cable, but even then, 3 cable failing in a few hours seem a bit too much.

Next, I'll try to recreate the RAID following this:

[http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/)

Luckily I have md5sum of all the files, so I can easily check the status of the array if I manage to bring it up after the failure...

---

### Post by alfonso78 on 2011-10-24
So, just as expected, badblocks found no errors:

```
$ sudo badblocks -v /dev/sdd
Checking blocks 0 to 1953514583
Checking for bad blocks (read-only test): done
Pass completed, 0 bad blocks found.

```

I run badblocks on one of the two disks that failed yesterday.

And now, the big disk, bring back the RAID without restart from scratch.

I'll follow instructions found here:
[http://kevin.deldycke.com/2008/07/heroic-journey-to-raid-5-data-recovery/](http://kevin.deldycke.com/2008/07/heroic-journey-to-raid-5-data-recovery/)

As expected, all disks are online now (the case in now open, I'm testing the theory that it's a temperature issue):

```
$ sudo fdisk -l /dev/sda

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b0eabb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001   fd  Linux raid autodetect

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06b8c42b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

$ sudo fdisk -l /dev/sdd

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  3907024064  1953512001   fd  Linux raid autodetect

$ sudo fdisk -l /dev/sde

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbca1224

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect


```

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[2] sde1[4](S) sdd1[5](S)
      5860535808 blocks

unused devices: <none>

```

```
$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 8d7c459a:fa4bed44:cced5de7:ca715931 (local to host NAS)
  Creation Time : Mon Oct 10 12:17:49 2011
     Raid Level : raid6
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Oct 23 23:50:17 2011
          State : active
 Active Devices : 2
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 2
       Checksum : d9fb5ef1 - correct
         Events : 38958

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8        1        3      active sync   /dev/sda1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8        1        3      active sync   /dev/sda1
   4     4       8       65        4      spare   /dev/sde1
   5     5       8       49        5      spare   /dev/sdd1

```

```
$ sudo mdadm /dev/md0 -a /dev/sda1
mdadm: re-added /dev/sda1

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda1[3] sdb1[2] sde1[4](S) sdd1[5](S)
      7814047744 blocks

unused devices: <none>
```

```
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Oct 10 12:17:49 2011
     Raid Level : raid6
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Oct 23 23:52:18 2011
         ** State : active, degraded, Not Started**
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 8d7c459a:fa4bed44:cced5de7:ca715931 (local to host NAS)
         Events : 0.38960

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       17        2      active sync   /dev/sdb1
       3       8        1        3      active sync   /dev/sda1

       4       8       65        -      spare   /dev/sde1
       5       8       49        -      spare   /dev/sdd1

```

```
$ sudo mdadm -S /dev/md0
mdadm: stopped /dev/md0

$ sudo mdadm -A /dev/md0
mdadm: /dev/md0 assembled from 1 drive and 2 spares - not enough to start the array.
```

This command tells at which "revision" of the array each disk is "stopped":

```
$ sudo mdadm -E /dev/sd[abde]1 | grep Event
         Events : 38958
         Events : 38960
         Events : 38960
         Events : 38960

```

And now the risky bit (from [http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/) ).

Just be extra careful yesterday I save the output of:

```
sudo fdisk -l /dev/sd[abde]
```

cause I want to make sure the disks are not changing names at each reboot.

So What I want is to use the last two up and running disks (sda and sdb) to recreate the array:

```
$ sudo mdadm --create /dev/md0 --verbose --level=6 --raid-devices=4 /dev/sda1 /dev/sdb1 missing missing
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: super1.x cannot open /dev/sda1: Device or resource busy
mdadm: failed container membership check
mdadm: device /dev/sda1 not suitable for any style of array

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[2](S) sdd1[5](S) sde1[4](S) sda1[3](S)
      7814047744 blocks

unused devices: <none>


```

so this didn't really work.


```
$ sudo mdadm --verbose --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error

```

so I decided to try something "big":

(keep in mind I want to start out of sda1 and sdb1 since sdd1 and sde1 where undergoing syncing when the array stopped working)

```
$ sudo mdadm --remove /dev/md0 /dev/sde1
mdadm: hot removed /dev/sde1 from /dev/md0

$ sudo mdadm --remove /dev/md0 /dev/sdd1
mdadm: hot removed /dev/sdd1 from /dev/md0

$ sudo mdadm --remove /dev/md0 /dev/sdb1
mdadm: hot remove failed for /dev/sdb1: Device or resource busy

$ sudo mdadm --remove /dev/md0 /dev/sda1
mdadm: hot remove failed for /dev/sda1: Device or resource busy

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda1[3] sdb1[2]
      3907023872 blocks

unused devices: <none>

sudo mdadm --verbose --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error


```

```
$ sudo mdadm --force --remove /dev/md0 /dev/sdb1
mdadm: hot remove failed for /dev/sdb1: Device or resource busy
$ sudo mdadm --force --remove /dev/md0 /dev/sda1
mdadm: hot remove failed for /dev/sda1: Device or resource busy


$ sudo mdadm --create /dev/md0 --assume-clean --level=6 --verbose --raid-devices=4 /dev/sda1 /dev/sdb1 missing missing
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: super1.x cannot open /dev/sda1: Device or resource busy
mdadm: failed container membership check
mdadm: device /dev/sda1 not suitable for any style of array

```

```
$ sudo mdadm --force --verbose --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error
```

Ok, now I found a new page of tips and commands:
[http://www.linuxforums.org/forum/servers/77867-eeek-cant-assemble-degraded-dirty-raid6-array.html#](http://www.linuxforums.org/forum/servers/77867-eeek-cant-assemble-degraded-dirty-raid6-array.html#)

my apologies, I know this seems weird, but I tried to play with /sys/block/md0/md/array_state trying to edit it but I couldn't write on the file as root.

and then I started to type a few commands without much clarity:

```
$ sudo mdadm --force /dev/md0 -a /dev/sda1
mdadm: cannot get array info for /dev/md0
$ sudo mdadm -S /dev/md0
mdadm: stopped /dev/md0
$ sudo mdadm --force /dev/md0 -a /dev/sda1
mdadm: cannot get array info for /dev/md0
$ sudo mdadm --force /dev/md0 -a /dev/sda1
mdadm: error opening /dev/md0: No such file or directory
$ sudo mdadm /dev/md0 -a /dev/sda1
mdadm: error opening /dev/md0: No such file or directory
```

but eventually:

```
$ sudo mdadm --create /dev/md0 --verbose --level=6 --raid-devices=4 /dev/sda1 /dev/sdb1 missing missing
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Mon Oct 10 12:17:49 2011
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid6 devices=4 ctime=Mon Oct 10 12:17:49 2011
mdadm: size set to 1953510400K
[B]Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
[/B]
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdb1[1] sda1[0]
      3907020800 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/2] [UU__]

unused devices: <none>

```

```
$ sudo mdadm --verbose --run /dev/md0
mdadm: failed to run array /dev/md0: Device or resource busy
$ sudo mdadm --force --verbose --run /dev/md0
mdadm: failed to run array /dev/md0: Device or resource busy
$ sudo mdadm -S /dev/md0
mdadm: stopped /dev/md0
$ sudo mdadm --force --verbose --run /dev/md0
mdadm: failed to run array /dev/md0: Invalid argument
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>
```

the encrypted device /dev/md0p1 does not exist, so I guess it's time to give up and rebuild the whole array from backups.

I tried my best! :(

---

### Post by alfonso78 on 2012-01-18
Just to give some closure and help others:

I decided the MB was faulty and changed it.

I connected the HD (both OS and RAID disks) to the new MB and since then no disk ever disappeared again.

BTW, maybe it has nothing to do with it, but a couple of days I found this thread: [http://forums.freebsd.org/showthread.php?t=1012](http://forums.freebsd.org/showthread.php?t=1012) and at some point it says:

> I eventually did: atacontrol reinit, atacontrol detach, atacontrol attach, atacontrol reinit
on that drive's channel (last 2 log entries are from reinit) and found the drive had vanished (checking at each step) and I was unable to make it reappear without a reboot.

---

### Post by alfonso78 on 2012-02-11
My MB is gone, so I cannot be sure. But there is a chance I was experiencing this bug:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=625922](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=625922)

---

