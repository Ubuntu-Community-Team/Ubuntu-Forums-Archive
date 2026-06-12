---
title: "vmap allocation failed"
date: 2009-10-18
forum: General Help
---

### Post by map7 on 2009-10-18
I'm running Ubuntu 904 32bit and lately the machine has been freezing up about once a week for the last month.

I've checked my messages log and this is what I found:
```
Oct 16 07:54:10 LTSP kernel: [170177.637603] __ratelimit: 22 callbacks suppressed
Oct 16 07:54:10 LTSP kernel: [170177.637606] vmap allocation failed: use vmalloc=<size> to increase size.
```


How do I increase my vmalloc?  

Here is my devices (using command lspci)
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation Device 042c (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```

This system also acts as an LTSP server to two clients at the moment.  It's Core 2 Duo E8400 with 4GB (3GB usable) ram.  I had trouble with using the 64bit version with 32bit clients.

---

### Post by Found on 2009-12-18
Bump. I've got the same issue.

---

### Post by map7 on 2009-12-18
I think I fixed this problem by removing all my swap space and the reallocating it again.

---

### Post by mariost on 2010-11-29
I'm going to post in this thread no matter it's old, otherwise ill be creating another.
This is starting to happen too often, no matter what i'm doing - i have experienced it during general use, gaming, and after i have left the pc for an hour doing nothing. Just when it happens i have no control of the computer whatsoever. And the "solution" the poster has given isn't quite of a solution to me - its not a sure fix and the bug can reappear after that. So, here is part of my /var/log/messages output:
```

Nov 29 14:30:03 discharge-lap kernel: [ 5629.770768] alloc_vmap_area: 15 callbacks suppressed
Nov 29 14:30:03 discharge-lap kernel: [ 5629.770772] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5629.816284] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5629.852953] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5629.889346] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5629.937425] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5629.979101] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5630.020372] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5630.059901] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:03 discharge-lap kernel: [ 5630.107312] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:04 discharge-lap kernel: [ 5630.143736] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:09 discharge-lap kernel: [ 5635.733370] alloc_vmap_area: 33 callbacks suppressed
Nov 29 14:30:09 discharge-lap kernel: [ 5635.733374] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:10 discharge-lap kernel: [ 5636.774068] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.579650] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.630054] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.676362] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.703403] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.741074] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.797579] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.835628] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:11 discharge-lap kernel: [ 5637.872845] vmap allocation for size 532480 failed: use vmalloc=<size> to increase size.
Nov 29 14:30:19 discharge-lap kernel: [ 5645.820696] [fglrx] IRQ 47 Disabled

Nov 29 14:32:31 discharge-lap kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 29 14:32:31 discharge-lap rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1375" x-info="http://www.rsyslog.com"] (re)start
Nov 29 14:32:31 discharge-lap rsyslogd: rsyslogd's groupid changed to 102
Nov 29 14:32:31 discharge-lap rsyslogd: rsyslogd's userid changed to 101
Nov 29 14:32:31 discharge-lap kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 29 14:32:31 discharge-lap kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 29 14:32:31 discharge-lap kernel: [    0.000000] Linux version 2.6.35-22-generic-pae (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 (Ubuntu 2.6.35-22.35-generic-pae 2.6.35.4)

```

There is it - the 14:32 messages are of the boot after the bug happened and i did a power button shutdown... Hope you can help me, this isn't a bug I can leave unattended!

---

