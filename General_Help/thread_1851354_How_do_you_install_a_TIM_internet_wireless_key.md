---
title: "How do you install a TIM internet wireless key?"
date: 2011-09-28
forum: General Help
---

### Post by OGAMIITTO on 2011-09-28
Hi all,
 
I use Ubuntu 9.1, and I have just bought a TIM wireless key for Ubuntu which connects via USB. But when I plug it in, although the green light flashes on the key to show it is connected, nothing else happens. How do I install it? 
 
Many thanks for any advice any of you may be able to offer.
 
Ogami

---

### Post by ajgreeny on 2011-09-28
You really should update your system as 9.10 is no longer supported, but to try to answer your question we need to know more about the TIM wireless chip.

Please open a terminal and run ```
lsusb
``` and then ```
sudo lshw -C network
``` which should tell us that much and give some clue to drivers needed.

---

### Post by OGAMIITTO on 2011-09-28
Hi Ajgreeny
 
Many thanks for the reply. Yes, I should update you are right but I have been on the move a lot. 
 
Here is what I got when I typed in the code you suggested:
 
lsusb:
&#12288;
Bus 001 Device 012: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
&#12288;
-C Network:
 
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: wmaster0
version: 02
serial: 00:18:de:18:04:b6
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
resources: irq:27 memory:dfdff000-dfdfffff
*-network
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:15:c5:6d:0a:72
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
resources: irq:17 memory:df9fe000-df9fffff

---

### Post by ajgreeny on 2011-09-28
This thread may help you with what appears a simple solution.  Good luck.
[http://ubuntuforums.org/showthread.php?t=1547833](http://ubuntuforums.org/showthread.php?t=1547833)

---

### Post by OGAMIITTO on 2011-09-29
Many thanks Ajgreeny. Your help is much appreciated.
 
Ogami

---

### Post by gandaran on 2011-09-29
> TIM wireless key
are you referring to mobile broadband dongle/key or just a wireless adapter
> Bus 001 Device 012: ID 12d1:1446 Huawei Technologies Co., Ltd. 
this device is mobile broadband, just run the network manager mobile broadband setup wizard then choose country and internet provider, that's about all you need to connect.

---

### Post by OGAMIITTO on 2011-09-30
Hi Gandaran,
 
Thanks for the suggestion. Yes I am referring to the dongle/key. 
 
I will try what you suggested now.
 
Many many thanks.
 
Ogami

---

