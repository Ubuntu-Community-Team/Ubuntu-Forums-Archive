---
title: "Can't Mount Windows 7 Partition"
date: 2012-03-28
forum: General Help
---

### Post by gerard187 on 2012-03-28
I can't mount my Windows 7 partition. I can boot into Windows 7 find. I also ran chkdsk in windows with no errors. I have no problems with my other partitions.

This is error get on start up and in syslog: 
```
Mar 28 10:51:41 gerard187-desktop udevd[10483]:
 '/sbin/blkid -o udev -p /dev/sdc5' [16227] terminated by signal 11 (Segmentation fault)
```

Some more from syslog:

```
Mar 28 10:51:12 gerard187-desktop kernel: [ 4132.662533] blkid[10474]: segfault at ffffffff9b461acc ip 00007fb3590ae3fe sp 00007fff76af67c0 error 4 in libblkid.so.1.1.0[7fb35909c000+21000]
Mar 28 10:51:41 gerard187-desktop udevd[10483]: '/sbin/blkid -o udev -p /dev/sdc5' [16227] terminated by signal 11 (Segmentation fault)
Mar 28 10:51:41 gerard187-desktop kernel: [ 4162.112092] blkid[16227]: segfault at ffffffff9be7179c ip 00007ff799e833fe sp 00007fffaf2259f0 error 4 in libblkid.so.1.1.0[7ff799e71000+21000]


Mar 28 11:35:41 gerard187-desktop udevd[316]: '/sbin/blkid -o udev -p /dev/sdc5' [862] terminated by signal 11 (Segmentation fault)
Mar 28 11:35:41 gerard187-desktop kernel: [   27.560693] blkid[862]: segfault at ffffffff9be5279c ip 00007fbd073033fe sp 00007fffb4b36ad0 error 4 in libblkid.so.1.1.0[7fbd072f1000+21000]


Mar 28 11:41:40 gerard187-desktop udevd[321]: '/sbin/blkid -o udev -p /dev/sdc5' [969] terminated by signal 11 (Segmentation fault)
Mar 28 11:41:41 gerard187-desktop kernel: [   27.300267] blkid[969]: segfault at ffffffff9c23b79c ip 00007ff512eda3fe sp 00007fffaa5a06f0 error 4 in libblkid.so.1.1.0[7ff512ec8000+21000]


Mar 28 11:55:27 gerard187-desktop kernel: [   27.347629] blkid[862]: segfault at ffffffff9bbf879c ip 00007f14b55073fe sp 00007fff9dc0ff50 error 4 in libblkid.so.1.1.0[7f14b54f5000+21000]
Mar 28 11:55:27 gerard187-desktop udevd[314]: '/sbin/blkid -o udev -p /dev/sdc5' [862] terminated by signal 11 (Segmentation fault)


Mar 28 13:53:15 gerard187-desktop udevd[322]: '/sbin/blkid -o udev -p /dev/sdc5' [848] terminated by signal 11 (Segmentation fault)
Mar 28 13:53:15 gerard187-desktop kernel: [   26.888877] blkid[848]: segfault at ffffffff9ac5379c ip 00007fdb9e10f3fe sp 00007fffef033740 error 4 in libblkid.so.1.1.0[7fdb9e0fd000+21000]
```



Ubuntu 11.10 x64

---

### Post by PhantomTurtle on 2012-03-28
I'm not completely sure how to interpret that output but if you have Ubuntu installed using Wubi then you cannot access the rest of the files on your Windows partitions.

---

