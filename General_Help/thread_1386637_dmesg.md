---
title: "dmesg"
date: 2010-01-20
forum: General Help
---

### Post by Cardale on 2010-01-20
I have been trying to get a better understanding of how my os is setup.  I ran dmesg and I am looking for weird messages so I can figure out stuff and stuff....so what does this mean?

```
[   15.513886] EDAC amd64_edac:  Ver: 3.2.0 Dec 10 2009
[   15.513980] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   15.513983] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   15.513986] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   15.513988]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   15.513989]     Might be a BIOS bug, if BIOS says ECC is enabled
[   15.513990]     Use of the override can cause unknown side effects.
[   15.514016] amd64_edac: probe of 0000:00:18.2 failed with error -22

```

```
[   17.750014] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   17.790092] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input8
[   21.723544] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.723549] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   21.723550] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   21.723552] vboxdrv: the usage of hardware performance counters by
[   21.723553] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
```

---

### Post by Yellow Pasque on 2010-01-21
The first block means you don't have ECC memory, which is common for non-server systems.

---

### Post by Cardale on 2010-01-21
alright anyone know the second..thanks btw.

---

