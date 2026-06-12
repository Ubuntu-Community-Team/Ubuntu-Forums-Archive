---
title: "Ubuntu shutting down randomly with gnome-settings segfault"
date: 2011-09-08
forum: General Help
---

### Post by Hotel on 2011-09-08
Hi

My computer keeps randomly shutting down after an upgrade to 11.04. 

I'm running ubuntu 11.04 64-bit gnome 3 on a dual boot (w/ Win 7) desktop.
My CPU is an i7 920 and I have 6GB of RAM, my motherboard is a Foxcom Flaming Blade.

This problem did occur during the short time I was using gnome classic as well and I haven't used unity on this install. The problem did not occur whilst running 10.10 and doesn't occur in Win 7.

Looking through my log files I am getting this error in the kernel before it shuts down:
```
Sep  8 00:17:31 HJED-PC kernel: [ 1646.638205] [Hardware Error]: Machine check events logged
Sep  8 00:24:35 HJED-PC kernel: [ 2070.272799] gnome-settings-[2030]: segfault at 7faac563fb10 ip 00007faac563fb10 sp 00007ffffd371848 error 14 in libdbus-1.so.3.5.4[7faac5caf000+42000]
Sep  8 00:24:45 HJED-PC kernel: Kernel logging (proc) stopped.
Sep  8 09:57:01 HJED-PC kernel: imklog 4.6.4, log source = /proc/kmsg started.
```

The last line is when the kernel reboots. Usually just prior to this error is a list of my CPU cores:
```
Sep  7 22:15:02 HJED-PC kernel: [19282.344721] CPU7: Core temperature above threshold, cpu clock throttled (total events = 1191610)
Sep  7 22:15:02 HJED-PC kernel: [19282.344724] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1191556)
Sep  7 22:15:02 HJED-PC kernel: [19282.357710] CPU0: Core temperature/speed normal
Sep  7 22:15:02 HJED-PC kernel: [19282.357714] CPU7: Core temperature/speed normal
Sep  7 22:18:47 HJED-PC kernel: [19506.316975] CPU6: Core temperature above threshold, cpu clock throttled (total events = 1871458)
Sep  7 22:18:47 HJED-PC kernel: [19506.316978] CPU3: Core temperature above threshold, cpu clock throttled (total events = 1871259)
Sep  7 22:20:02 HJED-PC kernel: [19581.534324] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1227363)
Sep  7 22:20:02 HJED-PC kernel: [19581.534327] CPU7: Core temperature above threshold, cpu clock throttled (total events = 1227419)
Sep  7 22:20:02 HJED-PC kernel: [19581.546285] CPU0: Core temperature/speed normal
Sep  7 22:20:02 HJED-PC kernel: [19581.546289] CPU7: Core temperature/speed normal
```
This varies slightly every time.

Any help would be greatly appreciated. 

Thanks,
HJED

---

### Post by Hotel on 2011-09-24
Bump...

Any help would be really appreciated, this issue is getting very annoying.

---

