---
title: "Use both SandyBridge On Chip GPU and Nvidia Card"
date: 2012-09-02
forum: General Help
---

### Post by jpastin on 2012-09-02
I have a 2nd Gen i5 (SandyBridge) which comes with an On-Chip GPU using the Intel i915 driver.  I also have an Nvidia GeForce 9500 PCIe card.  It seems that I can get either one or the other to work in Precise.  If I set the primary display init in the bios to the onboard one, then that works, but not the PCIe card.  If I set it to PCIe for primary init, then I get the opposite.  I have a z68 Chipset, so my understanding is that I should be able to use both.  I seem to have the best luck with the onboard one as primary init.  When I go into 'Displays' on 'System Settings' it actually shows the other display, but just as 'Unknown'.  When I run 'nvidia-settings', it says that the Nvidia driver is not being used.  

The system is detecting both cards.  Here is the relevant output from 'lshw':
```

*-display
             description: VGA compatible controller
             product: G96 [GeForce 9500 GT]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:f8000000-f8ffffff memory:d0000000-dfffffff memory:f6000000-f7ffffff ioport:cf00(size=128) memory:f9000000-f907ffff
*-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:fb400000-fb7fffff memory:e0000000-efffffff ioport:ff00(size=64)



```

Additionally, 'lsmod' shows that the nvidia module is being loaded.  Unfortunately, I have no idea where to proceed from here.

---

### Post by oldfred on 2012-09-03
Some have suggested this:

Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by jpastin on 2012-09-05
Thanks, but I don't think that is what I am looking for. I want each card to control a monitor separately.  that sounds more like an SLI equivalent type of setup.

---

