---
title: "Enable DVI support with Intel graphics."
date: 2010-11-07
forum: General Help
---

### Post by warfacegod on 2010-11-07
Very simply put, I need to use my TV as a monitor via DVI.

Using Meerkat 64. Here's some specs:

```
warfacegod                
    description: Desktop Computer
    product: Veriton L460
    vendor: Acer
    version: R01-A1
    serial: PSV5706006804053852702
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=001C2582-927A-2008-0124-015946000000
  *-core
       description: Motherboard
       product: G31
       vendor: Acer
       physical id: 0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R01-A1 (09/24/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fe980000-fe9fffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe780000-fe7fffff

```

*-display:1 is listed as UNCLAIMED. Because the Physical ID is 2.1, I'm fairly certain this is the DVI port. Do I need a driver for this to work?

Thanks in advance.

---

### Post by warfacegod on 2010-11-12
Bumpo.

---

### Post by efflandt on 2010-11-12
Does it **not** work if you boot with the TV connected and turned on with DVI (or HDMI if using DVI to HDMI cable) selected as input on the TV?  If you only have one display connected (or external display on a laptop) with default Intel or HDMI drivers, BIOS would use whichever one has a display (or external display on a laptop).

But if you have more than one display connected, Linux X Intel would usually use what it thinks is a common resolution that both displays can handle (typically 1024x768 in my experience) to mirror on both displays.

Even if using both outputs (laptop display and external VGA at same time in my case) it still shows "*-display:1 UNCLAIMED".

One thing missing is whether you actually tried have a problem, or if you have not even tried it.  If you do have a problem, start by looking at /var/log/Xorg.0.log.  Or if you have an /etc/X11/xorg.conf (none needed normally) maybe something there is interfering.

---

### Post by warfacegod on 2010-11-14
It does not work with only the TV connected (DVI only cable). I get the Manufacturer (Acer) logo screen but it's totally garbled. As soon as GRUB2 kicks in, the screen turns black. I've also tried using a VGA monitor to get into the OS and then switch to the TV. Same deal, totally black. No signal is being sent.

---

### Post by warfacegod on 2010-11-14
The xorg.conf file is blank, as it should be.

---

### Post by warfacegod on 2010-11-23
Bump.

---

### Post by warfacegod on 2010-11-28
Upsadaisy.

---

### Post by warfacegod on 2010-12-06
Solved because I give up after a month of only one response aside from me.

---

