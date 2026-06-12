---
title: "Screen goes black and becomes unresponsive at times"
date: 2011-02-21
forum: General Help
---

### Post by skyde77 on 2011-02-21
Hello all,

I have a very irritating problem that occurs only once in a while so it is hard to diagnose.
Once in a while my screen turns black and the returns as if nothing has happened. Some of the fonts might be "weird" but other than that everything works fine. This is not too bad but now the problem has gotten a bit worse. Again once in a while (rarer than with the mere screen-blackness) my screen turns black, then returns but this time nothing works ie. mouse and keyboard are non-responsive. The only way to get the computer running again is to press the power button until the whole computer shuts down and then do a normal boot.

The computer I am using is a new Dell Precision T1500 and a fresh 64 bit 10.10 Ubuntu.
The problems have occurred with gnone and kde so I guess that X is not an issue.
Is there some log somewhere I could read from regarding what exactly happened when the computer "tilted" so next time it happens I could try to debug this problem. And more importantly is there a log that I could read after I have had to boot the machine? The problem is very irritating since I cannot repeat it when I want to.

I am not sure what specs would be useful so here are some I got from lshw
*-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU         680  @ 3.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU         680  @ 3.60GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1200MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 133MHz 

*-memory                                                                                                     
          description: System Memory                                                                              
          physical id: e                                                                                          
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: KP223C-ELD
             vendor: Manufacturer00
             physical id: 0
             serial: 2D087832
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: KP223C-ELD
             vendor: Manufacturer01
             physical id: 1
             serial: 2B086C32
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: KP223C-ELD
             vendor: Manufacturer02
             physical id: 2
             serial: 29087632
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3

*-display
                description: VGA compatible controller
                product: RV620 [FirePro 2260]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:43 memory:d0000000-dfffffff memory:fbef0000-fbefffff ioport:e000(size=256) memory:fbec0000-fbedffff

---

