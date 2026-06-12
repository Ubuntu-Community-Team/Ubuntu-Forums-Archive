---
title: "Help! Wifi Turned off after update"
date: 2009-08-18
forum: General Help
---

### Post by ahchen101 on 2009-08-18
Hi all, 
my wifi was working perfectly until I recently updated my computer. now the wifi card looks like it is completely turned off. I have the gateway lt3103u and i don' think there is an actual button to turn the wifi card back on. Does anyone know how to turn it back on? Thank.

---

### Post by timcredible on 2009-08-18
well, if the update included a new kernel, then you need to re-add the wifi driver to the new kernel.  to test, at boot, pick the old kernel, if it works ok, then that's the problem.

---

### Post by ahchen101 on 2009-08-18
the driver is still there. the wifi card is just turned off. do you know how to undo the updates or turn the card back on?

---

### Post by oboedad55 on 2009-08-19
> **ahchen101 said:**
> the driver is still there. the wifi card is just turned off. do you know how to undo the updates or turn the card back on?

It may be a key combination. Maybe you can start here, [http://support.gateway.com/support/default.aspx](http://support.gateway.com/support/default.aspx)

Jon

---

### Post by ahchen101 on 2009-08-19
i looked through the gateway website and didn't find a keycode... tried booting up the previous kernel where my wifi card was active but still didn't turn on. any more suggestions?

---

### Post by ahchen101 on 2009-08-19
ok. i ran lshw -C network and got this: 
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:d7:d9:f1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.104 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:9a:7f:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:56:35:b1:28:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Apparently my wireless has been disabled after i updated ubuntu nbr. does anyone know how to enable the wireless? Thanks

---

