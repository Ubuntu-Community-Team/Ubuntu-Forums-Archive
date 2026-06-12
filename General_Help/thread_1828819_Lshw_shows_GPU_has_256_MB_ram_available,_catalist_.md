---
title: "Lshw shows GPU has 256 MB ram available, catalist shows 1GB (Actual size)"
date: 2011-08-19
forum: General Help
---

### Post by J V on 2011-08-19
Lshw:```
  *-display               
       description: VGA compatible controller
       product: Juniper [Radeon HD 5700 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:49 memory:e0000000-efffffff memory:fbdc0000-fbddffff ioport:ce00(size=**256**) memory:fbd00000-fbd1ffff
```Catalyst: Memory Size 1024 MB

Actual card: 1GB GDDR5

Why does lshw mistake the amount of gpu ram?

Will this have an effect on applications? (I imagine games will run much slower on a 256m gpu than on one with 1g at it's disposal)

---

### Post by gordintoronto on 2011-08-19
The Ioport has a size of 256. Not 256 MB, 256.

lshw does not display how much memory your video card has.

---

### Post by J V on 2011-08-20
Well hardinfo seems to think it's 256, so I presumed that was what lshw was referring to...

---

