---
title: "At boot mdadm starts array before all drives are ready == degraded"
date: 2011-07-07
forum: General Help
---

### Post by the Goat on 2011-07-07
I'm seeing an issue during boot up of one of my computers.  I think I have traced it to mdadm automatically starting the array before all the discs in the array are ready.  So it results in a degraded array that I have to manually stop and restart to get all the drives working in it.

My PC with ubuntu 11.04 (64bit) has nine hard drives.  One drive has the root & swap partitions.  The other eight drives are in a single raid6 array (/dev/md0) with two partitions (md0p1 & md0p2).

Four of the drives in the array are connected to an sata expansion card ([SYBA SY-PEX40008 PCI Express SATA II](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124027)).  Support for this card is built into the kernel and seems to work fine.  But the four drives connected to the card are missed when mdadm automatically starts the array.

The timing of mdadm starting the array and the initialization of the drives is a race condition.  Some times it works okay.  But usually it doesn't.  I think all I need to do it delay the start of mdadm just a little and it should work consistently.  But I'm not sure how to do this.

My issue looks a lot like [this bug report](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681) from a few years ago.

Here is a snip of my dmesg output showing the issue.  You can see drive sdi was initiated right when md0 was being started.
```
[   15.330076] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   15.336507] ata10.00: ATA-7: SAMSUNG HE103UJ, 1AA01113, max UDMA7
[   15.336552] ata10.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   15.343073] ata10.00: configured for UDMA/100
[   15.343197] scsi 9:0:0:0: Direct-Access     ATA      SAMSUNG HE103UJ  1AA0 PQ: 0 ANSI: 5
[   15.343371] sd 9:0:0:0: Attached scsi generic sg8 type 0
[   15.343379] sd 9:0:0:0: [sdi] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   15.343480] sd 9:0:0:0: [sdi] Write Protect is off
[   15.343482] sd 9:0:0:0: [sdi] Mode Sense: 00 3a 00 00
[   15.343527] sd 9:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.360124]  sdi: sdi1
[   15.360386] sd 9:0:0:0: [sdi] Attached SCSI disk
[   15.361667] xor: automatically using best checksumming function: generic_sse
[   15.410013]    generic_sse: 10212.400 MB/sec
[   15.410081] xor: using function: generic_sse (10212.400 MB/sec)
[   15.414377] md: raid6 personality registered for level 6
[   15.415108] md: raid5 personality registered for level 5
[   15.415151] md: raid4 personality registered for level 4
[   15.420932] md: raid10 personality registered for level 10
[   15.440735] bio: create slab <bio-1> at 1
[   15.440795] md/raid:md0: device sdb1 operational as raid disk 5
[   15.440839] md/raid:md0: device sdd1 operational as raid disk 7
[   15.440884] md/raid:md0: device sdc1 operational as raid disk 6
[   15.440928] md/raid:md0: device sde1 operational as raid disk 3
[   15.441530] md/raid:md0: allocated 8490kB
[   15.441621] md/raid:md0: not enough operational devices (4/8 failed)
[   15.441687] RAID conf printout:
[   15.441688]  --- level:6 rd:8 wd:4
[   15.441690]  disk 3, o:1, dev:sde1
[   15.441692]  disk 5, o:1, dev:sdb1
[   15.441693]  disk 6, o:1, dev:sdc1
[   15.441695]  disk 7, o:1, dev:sdd1
[   15.442010] md/raid:md0: failed to run raid set.
[   15.442054] md: pers->run() failed ...

```

---

