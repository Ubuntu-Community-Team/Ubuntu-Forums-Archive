---
title: "Lost my front USB ports in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by Footpenis on 2011-10-15
Hey folks,

Ubuntu doesn't recognize **** on my two front ports... they still give power but device get not recognized... It worked fine under 11.04 so... help!!!

here is what~$ lshw -C bus
tells me:


 *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff

---

### Post by Footpenis on 2011-10-17
OK, got em back, i donno why or how but there back

---

