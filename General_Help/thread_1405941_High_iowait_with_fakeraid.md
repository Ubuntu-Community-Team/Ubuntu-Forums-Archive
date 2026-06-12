---
title: "High iowait with fakeraid"
date: 2010-02-13
forum: General Help
---

### Post by agruman on 2010-02-13
When copying or extracting files my system is terrible sluggish and almost unusable.
After some research i found out that iowait got incredibly high during io, spikes above 90%.

Since im running on nvidia nf4 fakeraid 0 i suspect this is the problem, but how do i fix this?

Im running on karmic 64bit, but had the same problems with jaunty.

iostat:
```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.50    0.00    4.17   92.33    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               1.00         0.00         4.00          0         12
sdb             164.67      1621.33         2.67       4864          8
dm-0            359.00      1716.00         4.00       5148         12

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.00    0.00    5.00   93.00    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               2.67         0.00        17.33          0         52
sdb             186.67      2477.33        14.67       7432         44
dm-0            406.67      2402.67        17.33       7208         52

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.66    0.00    6.49   90.85    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               1.00         0.00         8.00          0         24
sdb             149.33      1988.00         5.33       5964         16
dm-0            284.00      1958.67         8.00       5876         24

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.33    0.00    4.67   92.00    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               2.33         0.00         9.33          0         28
sdb             110.33       752.00        13.33       2256         40
dm-0            183.67       732.00         9.33       2196         28

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.67    0.00    3.00   94.33    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               1.99         0.00         7.97          0         24
sdb             108.64       757.48        10.63       2280         32
dm-0            144.19       766.78         7.97       2308         24

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.33    0.00    6.00   92.67    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               3.33         0.00        21.33          0         64
sdb             120.33      1077.33        12.00       3232         36
dm-0            174.33      1077.33        21.33       3232         64


```

```

agruman@desktop:~$ sudo hdparm -tT /dev/mapper/nvidia_fagfecaj6 
/dev/mapper/nvidia_fagfecaj6:
 Timing cached reads:   1636 MB in  2.00 seconds = 818.50 MB/sec
 Timing buffered disk reads:  220 MB in  3.00 seconds =  73.32 MB/sec

agruman@desktop:~$ sudo hdparm -tT /dev/mapper/nvidia_fagfecaj6 
/dev/mapper/nvidia_fagfecaj6:
 Timing cached reads:   1722 MB in  2.00 seconds = 861.41 MB/sec
 Timing buffered disk reads:  224 MB in  3.02 seconds =  74.20 MB/sec

agruman@desktop:~$ sudo hdparm -tT /dev/mapper/nvidia_fagfecaj6 
/dev/mapper/nvidia_fagfecaj6:
 Timing cached reads:   1730 MB in  2.00 seconds = 864.96 MB/sec
 Timing buffered disk reads:  224 MB in  3.02 seconds =  74.29 MB/sec

```

Linux desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

---

