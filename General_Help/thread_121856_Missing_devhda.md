---
title: "Missing /dev/hda*"
date: 2006-01-26
forum: General Help
---

### Post by btt on 2006-01-26
Think I've broken my partition table, and am a little unsure of how to fix it.  I have a dual boot ubuntu-amd64, and WinXP.  Everything is working fine from my WinXP install (on /dev/hda1).  I can see all drives fine, and no errors appear to be present.  I have been having overheating issues, but have switched around some fans, got an HDD cooler, and all appears fine now.  Had a few hard lockups before I did this though.  I'm guessing that's what caused the problem.

Ubuntu has stopped detecting my hda partitions at boot:

```
btt@btt:/dev$ ls -F hd*
hda  hdb  hdb1  hdc
btt@btt:/dev$

```

Seems to find them fine after booting:

```
btt@btt:/dev$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/hda5            2551       12749    81923436    7  HPFS/NTFS
/dev/hda6           12750       15434    21567231    b  W95 FAT32
/dev/hda7           15435       18557    25085466    7  HPFS/NTFS
/dev/hda8           18558       18819     2104483+  82  Linux swap / Solaris
/dev/hda9           18820       19457     5124703+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4865    39078081   83  Linux
```

However, several errors are shown at boot (trimmed out irrelevant sections):

```
btt@btt:/dev$ dmesg

[   52.545272] Probing IDE interface ide0...
[   52.808577] hda: WDC WD1600BB-00GUA0, ATA DISK drive
[   53.063528] hdb: WDC WD400EB-00CPF0, ATA DISK drive
[   53.116390] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   53.116472] Probing IDE interface ide1...
[   53.788390] hdc: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive
[   54.400023] ide1 at 0x170-0x177,0x376 on irq 15
[   54.400104] Probing IDE interface ide2...
[   54.912911] Probing IDE interface ide3...
[   55.424814] Probing IDE interface ide4...
[   55.936716] Probing IDE interface ide5...
[   56.451729] hda: max request size: 1024KiB
[   56.463910] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[   56.465590] hda: cache flushes supported
[   56.465650]  /dev/ide/host0/bus0/target0/lun0:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.468352] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.468355] ide: failed opcode was: unknown
[   56.469924] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.469929] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.469932] ide: failed opcode was: unknown
[   56.472242] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.472246] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.472249] ide: failed opcode was: unknown
[   56.473635] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.473639] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.473642] ide: failed opcode was: unknown
[   56.474843] hdb: DMA disabled
[   56.524605] ide0: reset: success
[   56.535019] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.535023] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.535026] ide: failed opcode was: unknown
[   56.536601] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.536605] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.536608] ide: failed opcode was: unknown
[   56.538914] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.538918] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.538921] ide: failed opcode was: unknown
[   56.540304] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.540308] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.540311] ide: failed opcode was: unknown
[   56.590592] ide0: reset: success
[   56.593398] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.593403] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.593405] ide: failed opcode was: unknown
[   56.593410] end_request: I/O error, dev hda, sector 0
[   56.593413] Buffer I/O error on device hda, logical block 0
[   56.595020] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.595024] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.595027] ide: failed opcode was: unknown
[   56.596452] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.596456] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.596459] ide: failed opcode was: unknown
[   56.598775] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.598779] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.598781] ide: failed opcode was: unknown
[   56.600209] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   56.600213] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   56.600215] ide: failed opcode was: unknown
[   56.650580] ide0: reset: success
[   56.658571]  unable to read partition table
[   56.662756] hdb: max request size: 128KiB
[   56.682614] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63
[   56.682618] hdb: cache flushes not supported
[   56.682649]  /dev/ide/host0/bus0/target1/lun0: p1
```

So far, I've tried re-writing the partition table with fdisk, and:

```
btt@btt:/dev$ sudo sfdisk -V /dev/hda
partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 8: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 9: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/hda: OK
```

Any ideas how I can get my partitions to work again?  Or is this just an indication I've fryed this drive (which seems unlikely, as WinXP has no issues)?

---

