---
title: "Recovering data from mirror with failed disk."
date: 2009-08-01
forum: General Help
---

### Post by K_V_B on 2009-08-01
Hello all,



I have a disk that was part of a software mirror. I need to get the data off it. So I atached it to my Ubuntu system (8.04 LTS) using a USB -> SATA dongle.
My system recongized it, and started up raid device /dev/md0. However, I'm stuck. The system refuses to start the raid, so I can't access the data.

```
mdadm --detail /dev/md0 gives:

/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Aug 16 22:21:46 2006
     Raid Level : raid0
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug 16 22:21:47 2006
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : e729d30e:497d26d5:7561c100:4b5826ea
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       0        0        1      removed
```


One disk missing, so the raid is degraded, but that is to be expected. But I should be able to mount it, no?

```
# mount -t ext3  /dev/md0 /extra2 
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So I look at dmesg:
```

[ 4798.308857] md0: setting max_sectors to 128, segment boundary to 32767
[ 4798.308866] raid0: looking at sdf1
[ 4798.308868] raid0:   comparing sdf1(312568576) with sdf1(312568576)
[ 4798.308871] raid0:   END
[ 4798.308873] raid0:   ==> UNIQUE
[ 4798.308874] raid0: 1 zones
[ 4798.308876] raid0: FINAL 1 zones
[ 4798.308879] raid0: too few disks (1 of 2) - aborting!
[ 4798.308881] md: pers->run() failed ...
[ 6624.590238] EXT3-fs: unable to read superblock
```

So the raid is failed, because a disk is missing. But forcing a start should fix that, according to the manual:
```

# mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Cannot allocate memory
```

And here I'm stuck. What should I do? My system has 4GB of memory, so that it can't allocate memory is a bit odd...

What should I do? Is there another method of getting the data of the disk?

/proc/mdstat contains this:

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdc[1] sdb[0]
      1465138496 blocks [2/2] [UU]
      [========>............]  resync = 43.6% (639165248/1465138496) finish=127.1min speed=108275K/sec
      
md1 : active raid1 sde1[0] sdd1[1]
      732571904 blocks [2/2] [UU]
      
md0 : inactive sdf1[0](S)
      312568576 blocks
       
unused devices: <none>
```

Yes, there are other raid devices in this system ,but they funtion well. md2 is a new one I build (where I want to copy the data from md0 too...)

---

### Post by K_V_B on 2009-08-01
Ok. Need to get my foot out of my mouth. "Raid o" is stripe, not mirror. So I guess I'll have to get my data back from somwhere else :-(

---

