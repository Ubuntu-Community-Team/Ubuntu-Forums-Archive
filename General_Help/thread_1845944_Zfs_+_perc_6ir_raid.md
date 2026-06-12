---
title: "Zfs + perc 6ir raid"
date: 2011-09-18
forum: General Help
---

### Post by QuinRiva on 2011-09-18
I have a simple RAID 0 array that I use as a basically a temporary scratch disk for downloading and extracting files.  I do a lot rar extractions (100Gb per day), so the added speed from RAID0 is a benefit.  Today I must have bumped the case because one of the disks went offline (I think the power cable must have might not have been connected very tightly), I rebooted the machine and bam everything on the array is gone.

```
quinriva@Vanity:~$ sudo zpool status -v download
  pool: download
 state: FAULTED
status: The pool metadata is corrupted and the pool cannot be opened.
action: Destroy and re-create the pool from
        a backup source.
   see: http://www.sun.com/msg/ZFS-8000-72
 scan: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        download    FAULTED      0     0     2  corrupted data
          sdc       ONLINE       0     0    12

```

I tried clearing but I get an I/O error.  There is nothing wrong with the drives.  Anyway, it's not a huge loss of data but some of the files will take a couple of weeks to re-download.

I know RAID0 is risky, and if I have a drive fail I'll live with it, but I was hoping it would be a bit more robust in the event of a power failure.

Is there anyway to repair the array?

Also, say I want to run a daily backup to the network file-server, what's the best way of doing this?  I'm primarily concerned with backing up low seeded 50Gb torrents that can take a month to download.

---

