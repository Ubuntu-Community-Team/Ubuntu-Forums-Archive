---
title: "gparted-instant crash"
date: 2010-11-24
forum: General Help
---

### Post by ByteOneZero on 2010-11-24
ive searched the forums and web for info on this but i am stumped.not unusual since i started to use linux.gparted crashes after about 3 seconds of grayed out screentime.here is my terminal readout after entering sudo gparted command.tenza@tenza-desktop:~$ sudo gparted
[sudo] password for tenza: 
======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0x9e1f0a]
  15: /lib/libparted.so.0(+0x42507) [0xa19507]
  14: /lib/libparted.so.0(+0x43317) [0xa1a317]
  13: /lib/libparted.so.0(+0x4460c) [0xa1b60c]
  12: /lib/libparted.so.0(+0xf7b1) [0x9e67b1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x9ea032]
  10: /lib/libparted.so.0(+0x45fa3) [0xa1cfa3]
  9: /lib/libparted.so.0(+0x4619f) [0xa1d19f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x9eae15]
  7: /usr/sbin/gpartedbin() [0x80901e6]
  6: /usr/sbin/gpartedbin() [0x809fc9b]
  5: /usr/sbin/gpartedbin() [0x80c0532]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0xe3ceb2]
  3: /lib/libglib-2.0.so.0(+0x65def) [0x57edef]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0x60796e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x85aa4e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.
tenza@tenza-desktop:~$ 
anybody got any ideas???

---

### Post by ByteOneZero on 2010-12-01
i backed up my whole ubuntu10.04 setup onto an external hd.after this op was completed my desktop icon for gparted miraculously opened.wtf?anybody know or should i even care?i can mark this solved but the answer is still a mystery.:p

---

