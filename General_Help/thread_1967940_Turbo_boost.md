---
title: "Turbo boost"
date: 2012-04-28
forum: General Help
---

### Post by J V on 2012-04-28
So as far as I can tell *none* of the overclocking I've done in my uefi bios have stuck in linux:

```
$ grep -i mhz /proc/cpuinfo 
cpu MHz        : 1700.000
cpu MHz        : 3401.000
cpu MHz        : 3401.000
cpu MHz        : 2100.000
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000 
```

This despite a base clock of 3.5ghz and a turbo of 4.2.

I am on precise with a 3.2.0 kernel, and using a z77 mobo with an ivy bridge cpu.

Is this just not reporting correctly, or is it actually not working?

---

