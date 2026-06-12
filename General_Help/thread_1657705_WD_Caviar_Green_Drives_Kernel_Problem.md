---
title: "WD Caviar Green Drives Kernel Problem"
date: 2011-01-01
forum: General Help
---

### Post by esetnik on 2011-01-01
I have 4xWD20EARS which are the new 4k sector sata drives made by Western Digital.  I am running an old 500GB WD sata drive as my boot volume and these 4 drives will hopefully be in a software raid 5.  I am getting a kernel message during heavy disk access on each of the new drives:

```
Jan  1 15:05:48 mediaserver kernel: [  307.566686] ata1: hard resetting link
Jan  1 15:05:49 mediaserver kernel: [  307.921296] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  1 15:05:49 mediaserver kernel: [  307.929302] ata1.00: configured for UDMA/133
Jan  1 15:05:49 mediaserver kernel: [  307.929344] ata1: EH complete
Jan  1 15:05:49 mediaserver kernel: [  308.104397] ata1: hard resetting link
Jan  1 15:05:49 mediaserver kernel: [  308.451366] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  1 15:05:49 mediaserver kernel: [  308.459643] ata1.00: configured for UDMA/133
Jan  1 15:05:49 mediaserver kernel: [  308.459706] ata1: EH complete
Jan  1 15:05:49 mediaserver kernel: [  308.461113] ata1: hard resetting link
Jan  1 15:05:50 mediaserver kernel: [  308.810051] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  1 15:05:50 mediaserver kernel: [  308.817878] ata1.00: configured for UDMA/133
Jan  1 15:05:50 mediaserver kernel: [  308.817969] ata1: EH complete
Jan  1 15:05:50 mediaserver kernel: [  309.005623] ata1: limiting SATA link speed to 1.5 Gbps
Jan  1 15:05:50 mediaserver kernel: [  309.006639] ata1: hard resetting link
Jan  1 15:05:50 mediaserver kernel: [  309.351287] ata1: SATA link up <unknown> (SStatus 103 SControl 310)
Jan  1 15:05:55 mediaserver kernel: [  314.350060] ata1.00: qc timeout (cmd 0xec)
Jan  1 15:05:55 mediaserver kernel: [  314.350074] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jan  1 15:05:55 mediaserver kernel: [  314.350095] ata1: hard resetting link
Jan  1 15:05:56 mediaserver kernel: [  314.701289] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  1 15:05:56 mediaserver kernel: [  314.709706] ata1.00: configured for UDMA/133
Jan  1 15:05:56 mediaserver kernel: [  314.709807] ata1: EH complete
Jan  1 15:06:35 mediaserver kernel: [  353.719175] lo: Disabled Privacy Extensions
Jan  1 15:07:35 mediaserver kernel: [  414.285108] ata1: hard resetting link
Jan  1 15:07:36 mediaserver kernel: [  414.691288] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  1 15:07:36 mediaserver kernel: [  414.699725] ata1.00: configured for UDMA/133
Jan  1 15:07:36 mediaserver kernel: [  414.699835] ata1: EH complete
Jan  1 15:11:35 mediaserver kernel: [  654.532979] ata1: hard resetting link
Jan  1 15:11:36 mediaserver kernel: [  654.940084] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  1 15:11:36 mediaserver kernel: [  654.947758] ata1.00: configured for UDMA/133
Jan  1 15:11:36 mediaserver kernel: [  654.947806] ata1: EH complete
Hard Resetting LinkJan  1 15:11:40 mediaserver kernel: [  659.539467] ata1: hard resetting link
Jan  1 15:11:41 mediaserver kernel: [  659.881329] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan  1 15:11:41 mediaserver kernel: [  659.889020] ata1.00: configured for UDMA/133
Jan  1 15:11:41 mediaserver kernel: [  659.889130] ata1: EH complete

```

The drives do not even need to be formatted or partitioned for these errors to come up.  If I use disk utility to set the partition map to none and then benchmark the drives they all display these errors in console and the benchmark fails with IO errors.  When I try to write data to the drives, it becomes corrupted and unusable.  When I try to setup the raid array, it resyncs for 48 hours and then the drives fail to stay online.  They drop off at random during raid array formatting.  The boot drive works perfectly and never displays any error.

I have spent the last month searching for a solution including:
1.  New power supply
2.  New Sata cables
3.  Other Distros (It appears to be a kernel problem)

I contacted WD to see if I could return the drives and they said no, since they passed extended smart status test.

If anyone has any advice it would be greatly appreciated.

Thanks,
Ethan

---

### Post by esetnik on 2011-01-01
One thing I just noticed is that it appears to only occur during disk writes.

I wrote some photos to the disk in order to produce the above kernel output, and now I am copying them off the disk and haven't received any further kernel output.

---

### Post by esetnik on 2011-01-12
Anyone out there have any ideas for me?

---

### Post by dcstar on 2011-01-12
> **esetnik said:**
> Anyone out there have any ideas for me?

I use an older WD "Green" drive in an eSATA enclosure and I have no problems at all.

Are you using AHCI mode in your BIOS?

---

### Post by esetnik on 2011-01-12
I have confirmed AHCI Mode and not legacy IDE is enabled in the bios.

If it makes any difference, I am running an ASRock atom motherboard.

It is possible that your older Green drive does not use the new 4k sectors which have been giving linux users grief.  I am not sure that my issue is related to that new tech, but it is certainly a possibility.  Any other suggestions?

Right now I am considering buying a hardware raid card since I don't want to lose $400 on these drives.

I just hope that I don't buy one and still have issues.

---

