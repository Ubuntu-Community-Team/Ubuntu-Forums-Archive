---
title: "How do I setup memory correctly..?"
date: 2011-01-25
forum: General Help
---

### Post by r.osmanov on 2011-01-25
Hi there!

Please, tell me, if my setup is wrong. I've GYGABYTE 880GM-UD2H motherboard with four memory slots:
Slot-0: 4G 1333Mhz
Slot-1: 4G 1333Mhz
Slot-2: 2G 1333Mhz
Slot-3: 2G 1333Mhz
Slots 0 and 2 -- channel 0, and slots 1 and 3 -- channel 1. These should produce 12G. On x86_64 arch I expect it to be about 6G. But System Monitor shows 7.8G. Thus, it consumes 2G from each slot.

I had slots 0 and 1 with 4G cards each before. It was about 4G of total memory.

Should I leave 2G cards, or not?

Regards.

---

### Post by cariboo on 2011-01-25
Is all the ram detected during post?

---

### Post by r.osmanov on 2011-01-25
> **cariboo907 said:**
> Is all the ram detected during post?
I think it detected, but incorrectly: 
```
$ sudo lshw -C memory
  *-firmware              
       description: BIOS
       vendor: Award Software International, Inc.
       physical id: 0
       version: F4 (03/24/2010)
       size: 128KiB
       capacity: 960KiB
       capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: a
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L3 cache
       physical id: c
       slot: External Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: synchronous internal write-back
  *-cache
       description: L1 cache
       physical id: b
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-memory
       description: System Memory
       physical id: 25
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM 1333 MHz (0.8 ns)
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: DIMM 1333 MHz (0.8 ns)
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:2
          description: DIMM 1333 MHz (0.8 ns)
          product: None
          vendor: None
          physical id: 2
          serial: None
          slot: A2
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:3
          description: DIMM 1333 MHz (0.8 ns)
          product: None
          vendor: None
          physical id: 3
          serial: None
          slot: A3
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
```

---

