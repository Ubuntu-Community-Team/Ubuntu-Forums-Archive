---
title: "Time deported by dmesg"
date: 2009-08-09
forum: General Help
---

### Post by thomasf on 2009-08-09
Hi!

I noticed a discontinuity in time reported by dmesg.

```

[    0.000000] Kernel command line: root=/dev/md0 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] NR_IRQS:2304
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[B][    0.000000] Detected 2698.896 MHz processor.
[   30.427820] Console: colour VGA+ 80x25[/B]
[   30.427822] console [tty0] enabled
[   30.428098] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   30.428515] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.433675] allocated 20971520 bytes of page_cgroup

```

As you can see, dmesg output shows a 30 second gap, however this gap is purely virtual. There is no delay during booting.
I wonder what is the source of this "phenomenon" :) On stock kernel everything is fine.
Some platform details: Ubuntu 9.04, kernel 2.6.30.4, x86_64, RAID0 (Linux sofware RAID)
Any ideas?

Cheers,
Thomas

---

