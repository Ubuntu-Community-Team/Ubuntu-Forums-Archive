---
title: "power top wake ups from  [kernel scheduler] Load balancing tick and [ohci_hcd:usb4,"
date: 2010-08-07
forum: General Help
---

### Post by markp1989 on 2010-08-07
trying to save abit of power where i can, this is from my fileserver/htpc, a zotac gf 9300 itx motherboard and a underclocked e3300 at 100mhz on fsb.


is there any way i can lower the amounnt that these processes wake up the cpu?



```

< Detailed C-state information is not P-states (frequencies)
                                        1250 Mhz     0.1%
                                        1000 Mhz     0.0%
                                         800 Mhz     0.0%
                                         600 Mhz    99.8%


Wakeups-from-idle per second : 67.1     interval: 10.0s
no ACPI power usage estimate available
Top causes for wakeups:
  42.2% ( 37.8)   [kernel scheduler] Load balancing tick
  34.6% ( 31.0)   [ohci_hcd:usb4, nvidia] <interrupt>
   5.5% (  4.9)   [kernel core] hrtimer_start (tick_sched_timer)
   3.3% (  3.0)   xbmc.bin
   3.0% (  2.7)   rtorrent
   2.2% (  2.0)   [kernel core] clocksource_watchdog (clocksource_watchdog)

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.
 Q - Quit   R - Refresh   S - SATA Link Power Management 

```

thanks, mark

edit: is there away to get this cpu to run in Cstates?

---

### Post by colin.p on 2010-08-07
I wish mine was only 67 or so. Take a look at mine.

  [HTML]
     PowerTOP version 1.12      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 5.1%)         2.21 Ghz     0.8%
polling           0.0ms ( 0.0%)         1.60 Ghz     0.0%
C1 mwait          0.6ms ( 1.8%)         1200 Mhz    99.2%
C3 mwait          2.1ms (93.1%)


Wakeups-from-idle per second : 485.6    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  24.5% ( 97.6)   [eth1] <interrupt>
  16.8% ( 66.8)   [kernel scheduler] Load balancing tick
   1.8% (  7.2)D  transmission
   8.6% ( 34.4)   [ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb6] <interrupt>
   7.8% ( 31.0)   USB device 2-3.1 : USB Optical Mouse (Logitech)
   0.0% (  0.0)D  flush-8:0

[/HTML]

From what I can gather it's the 2.6.32-24 kernel in lucid (and maybe other distros as well?)and they are aware of the problem. I guess a newer kernel, like the one in maverick, is supposed to address the issue. Whether it completely fixes the issue, remains to be seen. Anyway there is alot of different threads about it.

---

### Post by colin.p on 2010-10-14
Just to revive an old ongoing issue, how is maverick's kernel handling this problem? Is the wake - ups and load - balancing better handled in maverick?
The only computer that would benefit from this is my laptop, which would be the only one I would consider upgrading. The others I am leaving on lucid, as there is no reason to go to maverick on them.

---

### Post by oldmankit on 2010-11-09
I'm using maverick and am having the same problem.  I'm just starting to look into it.

```
  45.6% (341.0)   [kernel scheduler] Load balancing tick
```

---

### Post by SaintDanBert on 2011-01-14
I'm only seeing 16% or so for the "load balancing tick" but I see
roughly 30% for "extra timer interrupt".

Even with that, I'm seeing 90% in C3 and 10% in C0. I've never seen
the 2-3% C0 that others report.

Puzzled,

~~~ 0;-Dan

---

