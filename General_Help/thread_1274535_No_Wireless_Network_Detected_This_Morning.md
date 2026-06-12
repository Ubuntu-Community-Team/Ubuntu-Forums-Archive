---
title: "No Wireless Network Detected This Morning"
date: 2009-09-24
forum: General Help
---

### Post by zamasama on 2009-09-24
My Laptop can't detect my wireless network i think it might be because of some updates but im not sure.

lspci output:
> 04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


---

### Post by gismo93 on 2009-09-24
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

that helped me when i had the same problem.

just try to follow the instruction step by step and hopefully shud get you up and going again

---

### Post by zamasama on 2009-09-24
Still No Luck myabe this could have some clue about my problem

lshw -C network output:
> 
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0



---

