---
title: "Lots of error messages during shutdown"
date: 2012-05-12
forum: General Help
---

### Post by JdeP on 2012-05-12
I am running 12.04 with dual 22" monitors. The hardware is fairly old, and the graphics card is unable to run Unity 3D. The system worked fine using Unity 2D and the installed Open Source driver, but with help from this forum I tried getting 3D to work using the proprietary driver. That didn't work at all, so I reverted to the Open Source one. Mostly the monitors now behave fine, but when I shut down there is often a long pause, and then after the screens go black there is a very long list of fast-moving error messages, so clearly something is not right. Ideally I'd like to go back to the "clean" Open Source setup I had before I tried the other driver.

So, if anyone's willing to help, how do I get at the error messages you'll need to diagnose this?

Thanks in advance,

Peter

Here's what lshw says about the graphics card:
```
        *-pci:1
             description: PCI bridge
             product: PT890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:e000(size=4096) memory:fe900000-fe9fffff memory:c0000000-cfffffff
           *-display
                description: VGA compatible controller
                product: RV630 [Radeon HD 3600 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:24 memory:c0000000-cfffffff memory:fe9e0000-fe9effff ioport:e000(size=256) memory:fe9c0000-fe9dffff
           *-multimedia
                description: Audio device
                product: RV635 HDMI Audio [Radeon HD 3600 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:65 memory:fe9fc000-fe9fffff


```

---

### Post by JdeP on 2012-05-27
> **JdeP said:**
> I am running 12.04 with dual 22" monitors. The hardware is fairly old, and the graphics card is unable to run Unity 3D. The system worked fine using Unity 2D and the installed Open Source driver, but with help from this forum I tried getting 3D to work using the proprietary driver. That didn't work at all, so I reverted to the Open Source one. Mostly the monitors now behave fine, but when I shut down there is often a long pause, and then after the screens go black there is a very long list of fast-moving error messages, so clearly something is not right. Ideally I'd like to go back to the "clean" Open Source setup I had before I tried the other driver.

So, if anyone's willing to help, how do I get at the error messages you'll need to diagnose this?

Thanks in advance,

Peter

Here's what lshw says about the graphics card:
```
        *-pci:1
             description: PCI bridge
             product: PT890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:e000(size=4096) memory:fe900000-fe9fffff memory:c0000000-cfffffff
           *-display
                description: VGA compatible controller
                product: RV630 [Radeon HD 3600 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:24 memory:c0000000-cfffffff memory:fe9e0000-fe9effff ioport:e000(size=256) memory:fe9c0000-fe9dffff
           *-multimedia
                description: Audio device
                product: RV635 HDMI Audio [Radeon HD 3600 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:65 memory:fe9fc000-fe9fffff


```

Bump

---

### Post by kc1di on 2012-05-27
you didn't say what the driver driver name was but this is worth a try.
in terminal type ```
sudo apt-get purge (name of driver you installed.)
```

The reason for the purge command is to remove the driver file and all it's configuration files also. you may get the message driver not installed in which case re install it and then purge it. 

Give that a try not for sure of course but may work.

---

