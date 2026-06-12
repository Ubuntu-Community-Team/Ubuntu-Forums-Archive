---
title: "what can one do if network manager disappears"
date: 2010-07-05
forum: General Help
---

### Post by shantiq on 2010-07-05
my network manager disappeared earlier on today after i clicked on hibernate which would not restore



so i turned everything off and restarted and NO network manager



went systems/preferences/network connections and no good

no internet


had to do a clean install after 4 attempts

my question is:


if it ever happened again how can one restore network manager and the all-important internet connection

i did lshw and got ```
*-network DISABLED
```

AND NOW after new install it gives me

```
 *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.100 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:20 ioport:8400(size=256) memory:ff3fec00-ff3fecff memory:9c000000-9c00ffff(prefetchable)

```






how could i have reenabled THE NETWORK from the command-line anyone knows the code?


thanx in advance      shan

---

### Post by happyhamster on 2010-07-05
Try:

sudo service network-manager stop
sudo service network-manager start

[edit: and make sure the network-manager is enabled in System-->Preferences-->Startup Applications-->Network Manager]

---

### Post by shantiq on 2010-07-05
thanx hamster


also found this which i guess would work too if one change the word disable for enable

system/preferences/startup applications

---

