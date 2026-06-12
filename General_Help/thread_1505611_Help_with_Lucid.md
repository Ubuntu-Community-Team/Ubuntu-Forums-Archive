---
title: "Help with Lucid?"
date: 2010-06-09
forum: General Help
---

### Post by CharlesJWelsh on 2010-06-09
Low Graphics Mode... Or a Screen that says "Pulseaudio configured for per user sessions"? IDK How to fix these issues... 
```
 
description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:10 memory:d8000000-dfffffff(prefetchable) memory:d0000000-d007ffff ioport:eff8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:20000000-27ffffff(prefetchable) memory:2c000000-2c07ffff

```

My display stuff ><

---

### Post by dino99 on 2010-06-09
*** "Pulseaudio configured for per user sessions" ***

thats the normal config, its an info not an error

about low graphic:

sudo rm -f /etc/X11/xorg.conf

check the driver is activated: system admin hardware driver

---

### Post by CharlesJWelsh on 2010-06-09
I ran the command and nothing happened... And it says i have no proprietary drivers...

---

