---
title: "Graphics screw up...."
date: 2010-03-13
forum: General Help
---

### Post by pingu1 on 2010-03-13
Hi!
I have been (in retrospect) screwing around with drivers and various packages in Synaptics on a Fujitsu Siemens ESPRIMO Mobile, which has a SiS graphic card

Now I get a normal boot up until about 5 seconds after the Ubuntu-mark shows up in the middle of the screen. After that the screen flickers and goes on and off, without any results. This just continues forever, without any solution.

I have tried the recovery mode, and tried to remember which packages I installed, and then tried to remove them, without success.

Any tips on what to do, except reinstall?

---

### Post by pingu1 on 2010-03-13
I managed to remove the drivers causing problems in recovery mode in the command-line.
An output of lshw shows this on the graphics-card:
> *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:d4000000


How do I know which graphics-driver it runs on now from this?
My resolution is 1280x800.

---

