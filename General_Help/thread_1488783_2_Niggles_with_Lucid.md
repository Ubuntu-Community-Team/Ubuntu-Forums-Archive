---
title: "2 Niggles with Lucid"
date: 2010-05-20
forum: General Help
---

### Post by DenisHillier on 2010-05-20
Hullo,
Just upgraded to Lucid and it's working fine apart from two niggles. 

1) I'm now seeing what looks like static on an analog TV set where I used to see the bootsplash

2)This was a problem before I upgraded but if I leave the computer on without rebooting for longer than about ten hours, the hard drive suddenly becomes read-only and I need to reboot and run fsck.

Some possibly relevant info about my hardware:

> 
description: Notebook
    product: X58C
    vendor: ASUSTeK Computer Inc.
    version: 1.0



*-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:fd6e0000-fd6fffff ioport:cc00(size=128)

*-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:43:50:e3:d7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:fd7f0000-fd7fffff


The second problem may be something to do with the Wireless, I had problems with it causing Ubuntu to freeze if I didn't disable and re-enable it on start up with previous versions, but the upgrade seems to have fixed this. 

Testing to see if the Wireless is a cause would involve leaving my computer idle for hours on end without being connected to the Internet to see if it makes a difference, I'm sure you can understand why I haven't done this. 

Any advice on how I might remedy these annoyances will be gratefully received.

---

### Post by mikewhatever on 2010-05-20
So, if I understand correctly, you've upgraded to a newer version of Ubuntu, and it fixed the two 'niggles' you had had. Are there any problems with the newer release?

---

