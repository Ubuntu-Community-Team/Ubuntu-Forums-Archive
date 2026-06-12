---
title: "Wireless problems not found in Ubuntu"
date: 2011-08-12
forum: General Help
---

### Post by zamadatix on 2011-08-12
Hello, I installed Lubuntu onto my laptop after finding the default Ubuntu install a bit bulky and slow for the machine only to be met with wireless problems. In the Ubuntu install I was simply able to click the wireless icon and found my routers SSID but in lubuntu I see nothing.

sudo lshw output for the wireless device:

*-network
	 description: Wireless interface
	 product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
	 vendor: Atheros Communications Inc.
	 physical id: 0
	 bus info: pci@0000:03:00.0
	 logical name: wlan0
	 version: 01
	 serial: 00:22:68:93:af:d9
	 width: 64 bits
	 clock: 33MHz
	 capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
	 configuration: broadcast=yes driver=ath5k driverversion=3.0.0-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
	 resources: irq:19 memory:f6000000-f600ffff

---

### Post by JC Cheloven on 2011-08-16
Hi, it seems strange. AFAIK the wireless support should be identical in ubuntu and lubuntu. Both use network manager as well.. 

Your card is supported though. It's installed in several [ubuntu certified machines]("http://www.ubuntu.com/certification/catalog/component/pci:001C:168C-NETWORK").

The driver in use for your card should be ath5k. Please see if that module is in use in your linux kernel. It should appear by typing at terminal
```
lsmod
```
If it isn't we can try to load it with modprobe later. But first, could you please post the output of these:```
ifconfig
``` ```
iwconfig
```

---

