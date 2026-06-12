---
title: "Kernel panic at boot"
date: 2010-04-07
forum: General Help
---

### Post by crazyfuturamanoob on 2010-04-07
**_Edit: The PC is broken and I'll buy a new one. Don' bother reading this thread._**

I have Kubuntu 9.10 installed on my Acer 7520g laptop. It used to work fine.

But recently my laptop has often went into kernel panic, sometimes at boot, sometimes after hours of normal usage. Today it has not been able to boot properly from HD a single time.

When I boot it up in recovery mode, it kernel panics and displays this (normal mode displays just the graphical progress bar, no text):
```

00010c0f
[    9.620019] TSC f0ed3f8e6
[    9.620019] PROCESSOR 2:60f82 TIME 1270650316 SOCKET 0 APIC 0
[    9.620019] This is not a software problem!
[    9.620019] Run through mcelog --ascii to decode and contact your hardware vendor
[    9.620019] Machine check: Processor context corrupt
[    9.620019] Kernel panic - not syncing: Fatal machine check on current CPU
[    9.620019] Pid: 0, comm: swapper Tainted: G    M     2.6.31-14-generic #48 Ubuntu
[    9.620019] Call Trace:
[    9.620019] <#MC> [<ffffffff81426a29>] panic+0x73/0x12b
[    9.620019] [<ffffffff81426a29>] mce_panic+0x16a/0x190
[    9.620019] [<ffffffff81426a29>] do_machine_check+0x637/0x68
[    9.620019] [<ffffffff81426a29>] machine_check+0x1c/0x30
[    9.620019] [<ffffffff81426a29>] ? native_safe_halt+0x6/0x10
[    9.620019] <<EOE>> [<ffffffff81426a29>] default_idle+0x4c/0xe0
[    9.620019] [<ffffffff81426a29>] ? clockevents_notify+0x49/0xa0
[    9.620019] [<ffffffff81426a29>] c1e_idle+0x9a/0x120
[    9.620019] [<ffffffff81426a29>] cpu_idle+0xb2/0x100
[    9.620019] [<ffffffff81426a29>] rest_init+0x66/0x70
[    9.620019] [<ffffffff81426a29>] start_kernel+0x352/0x35b
[    9.620019] [<ffffffff81426a29>] x86_64_start_reservations+0x125/0x129
[    9.620019] [<ffffffff81426a29>] x86_64_start_kernel+0xfa/0x109

```
I copied it by hand so there might be typos, especially in the hex codes.

I'm sure this is a pure software problem, because Ubuntu 7.10 LiveCD boots up normally and I got X, Gnome and everything working. So CPU must be working perfectly.

I read the logs in /var/log but there were no error messages. How to fix this? I will post all information you need.

---

### Post by crazyfuturamanoob on 2010-04-10
Bump. Could it be malfunctioning nvidia drivers? Driver version was 185.xx, while the latest version is 195.36.15.

Sometimes when selecting a kernel at grub menu, it loads something for 15 seconds then reboots.

---

### Post by crazyfuturamanoob on 2010-04-14
I tried re-installing Kubuntu 2 times. Same error as before when booting the fresh install from hard disk. Then I tried installing Arch Linux. Very basic system, no GUI, no X, no nvidia drivers, just terminal. It still didn't work.

This must be a hardware problem so I give up and send the laptop for repairs.

---

### Post by 98cwitr on 2010-04-14
run memtest86

---

### Post by crazyfuturamanoob on 2010-04-18
Memtest86+ worked fine and reported no errors, but I already sent the laptop away.

---

