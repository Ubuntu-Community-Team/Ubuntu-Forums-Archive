---
title: "Cannot connect to internet (wireless)"
date: 2009-11-17
forum: General Help
---

### Post by nayeret43 on 2009-11-17
I have a Aspire 5735-4774 laptop with Ubuntu 9.04 installed on it.  And I have been able to connect to the internet up until last night.  And I have no clue why.

I have enabled networking and wireless, and my laptop **does** recognize the networks, but it won't connect (even though up until last night it connected no problem).  It is a secured network, but I have the password, so that's not the problem either.

_Here is what I did:_

I went to the troubleshooting part of the 'Ubuntu Help' (for wireless - section 5.2) and the first step was to check that the device is on.

So I typed in the terminal > sudo lshw -C network

It said that I would see an output, along with the words "CLAIMED,UNCLAIMED, ENABLED or DISABLED".

This was the output:

> *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:cb:51:c7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:47:eb:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:9c:62:82:a7:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



So apparently, my wireless device is off (because it said 'DISABLED' on the output).  It says in the help that I may need to turn on a switch or something, but there is nothing physical on my laptop that I need to switch on for wireless.


What should I do?  Why would the internet suddenly stop working like that?

---

