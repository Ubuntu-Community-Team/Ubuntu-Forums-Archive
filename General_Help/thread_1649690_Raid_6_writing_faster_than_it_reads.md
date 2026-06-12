---
title: "Raid 6 writing faster than it reads"
date: 2010-12-20
forum: General Help
---

### Post by whoopn on 2010-12-20
Ok first off the write speeds are off the hook, 210MB/s on 5400RMS disks (5 disks in a RAID 6). However, read speeds are 68MB/s.  I wondering first off, why? and secondly could this be an indicator of something not properly setup that might cause harm to my disks?

---

### Post by SaturnusDJ on 2010-12-20
No idea but you should post more information about your config, how you benchmarked, etc.

---

### Post by whoopn on 2010-12-20
I tested using dd,

ie:

dd if=/dev/zero of=/path/to/raid/mount/point/test.txt bs=1M count=12000

I have 4GB of RAM so I wanted to make sure it wasn't cache throwing off the results.

---

### Post by mr clark25 on 2010-12-20
i would try using hdparm:
```

hdparm -Tt /dev/sdXY

```

this will also show the drive cache reads, which should be relatively fast on raid 6.

---

### Post by whoopn on 2010-12-20
Timing cached reads:   8046 MB in  2.00 seconds = 4025.20 MB/sec
 Timing buffered disk reads:  238 MB in  3.00 seconds =  79.32 MB/sec

Is that what you're looking for?

---

### Post by tgalati4 on 2010-12-20
That is odd.  Your read speeds should be the same or faster than your write speeds.

What kind of disks?  Make and Model, also IDE, SATA, or SCSI?

What RAID controller?  If hardware RAID, what settings did you use in RAID BIOS?

There are more detailed tests that can be run by installing phoronix-test-suite.

Check dmesg for any errors or I/O waits.

man vmstat for ways to dig into disk performance.

---

