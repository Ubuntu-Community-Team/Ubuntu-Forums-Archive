---
title: "GParted is crashing on startup."
date: 2010-11-26
forum: General Help
---

### Post by sirspazzolot on 2010-11-26
```

matt@Matt:~$ gksu gparted
======================
libparted : 2.3
======================
Backtrace has 15 calls on stack:
  15: /lib/libparted.so.0(ped_assert+0x2a) [0xc4b87a]
  14: /lib/libparted.so.0(ped_geometry_read+0x116) [0xc555e6]
  13: /lib/libparted.so.0(hfsplus_probe+0x3a1) [0xc75751]
  12: /lib/libparted.so.0(ped_file_system_probe_specific+0x6c) [0xc4d3dc]
  11: /lib/libparted.so.0(ped_file_system_probe+0x81) [0xc4d9d1]
  10: /lib/libparted.so.0(+0x44d9f) [0xc86d9f]
  9: /lib/libparted.so.0(+0x44fcf) [0xc86fcf]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xc547d5]
  7: /usr/sbin/gpartedbin() [0x8090126]
  6: /usr/sbin/gpartedbin() [0x80a06b5]
  5: /usr/sbin/gpartedbin() [0x80c1f42]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x539e42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0x6a448f]
  2: /lib/libpthread.so.0(+0x5cc9) [0x4f2cc9]
  1: /lib/libc.so.6(clone+0x5e) [0xfe26be]

```
Same thing happens if I use sudo or after su root. It prompts me for my password to do administrative tasks, the GUI pops up for a second, looking like it's scanning stuff, and then disappears. That's what happens in the terminal. I'm running 10.10. Reinstalling did nothing. No big deal if I can't get it fixed; I have a parted magic LiveCD and a backtrack liveCD and a backtrack install with working thingers. Thanks for any responses here though.

---

### Post by Quackers on 2010-11-26
Did you try just entering gparted into the terminal?
Is Gparted installed on your system?

---

### Post by sirspazzolot on 2010-11-26
DURRRRR. Yes it is installed. Just GParted gives ```
matt@Matt:~$ gparted
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon 
``` but I don't really think that matters, considering you need administrative privileges to use GParted so this is a predictable result.

---

### Post by Quackers on 2010-11-26
Sorry! sudo gparted works for me :-)

---

### Post by sirspazzolot on 2010-11-26
oh well. Thanks anyway.

---

