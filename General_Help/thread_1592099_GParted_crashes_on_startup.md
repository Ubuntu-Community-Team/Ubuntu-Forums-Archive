---
title: "GParted crashes on startup?"
date: 2010-10-10
forum: General Help
---

### Post by sirspazzolot on 2010-10-10
DISCLAIMER: I know I should go to the gparted forums for this question. I'm at the ubuntu forums though because I think the reason is that Ubuntu is somehow conflicting with my BackTrack linux installation; it worked fine before I installed it.

Reinstalling did nothing. Trying to run from Terminal gives:
```
matt@Matt:~$ gparted
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon
matt@Matt:~$ sudo gparted
[sudo] password for matt: 
======================
libparted : 2.3
======================
Backtrace has 15 calls on stack:
  15: /lib/libparted.so.0(ped_assert+0x2a) [0xb9d87a]
  14: /lib/libparted.so.0(ped_geometry_read+0x116) [0xba75e6]
  13: /lib/libparted.so.0(hfsplus_probe+0x3a1) [0xbc7751]
  12: /lib/libparted.so.0(ped_file_system_probe_specific+0x6c) [0xb9f3dc]
  11: /lib/libparted.so.0(ped_file_system_probe+0x81) [0xb9f9d1]
  10: /lib/libparted.so.0(+0x44d9f) [0xbd8d9f]
  9: /lib/libparted.so.0(+0x44fcf) [0xbd8fcf]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xba67d5]
  7: /usr/sbin/gpartedbin() [0x8090126]
  6: /usr/sbin/gpartedbin() [0x80a06b5]
  5: /usr/sbin/gpartedbin() [0x80c1f42]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x4f7e42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0xa5548f]
  2: /lib/libpthread.so.0(+0x5cc9) [0xae7cc9]
  1: /lib/libc.so.6(clone+0x5e) [0x10b06ae]

```
and GParted pops up for like a second and then exits.

Halp? Is it conflicting with BackTrack somehow or am I wrong?

---

### Post by bprins on 2010-10-10
got an ubuntu live CD?

try to run gparted from ubuntu live, then you also don't have to bother unmounting used partitions while running ubuntu.

doesn't solve your problem of course, but maybe you'll settle for a viable work-around :)

---

### Post by sirspazzolot on 2010-10-10
Yeah, I've been using an Ubuntu liveCD but I need to do stuff to an HFS+ partition and that hasn't worked from a livecd. I'll just find some way to do it anyway. thanks :)

---

