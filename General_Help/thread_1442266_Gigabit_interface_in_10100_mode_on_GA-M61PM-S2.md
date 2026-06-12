---
title: "Gigabit interface in 10/100 mode on GA-M61PM-S2"
date: 2010-03-29
forum: General Help
---

### Post by covert on 2010-03-29
I have Mythbuntu 9.10 on a GA-M61PM-S2 motherboard. I have a gigabit switch with line speed indication LED's. When I plug in my desktop it shows I have a gigabit connection (as expected) but when I plug in the Mythbuntu Machine it only shows my link speed as 10/100. I have also switch network cables and ports on the switch.

I started a file transfer and I am only getting 10/100 speeds (90Mbits/s)

I have checked the bios and I cannot find any settings for switching on gigabit on the network interface.

A search of this forum and google has not helped.

Is there an extra setting / command I need to do to enable gigabit speeds ?

---

### Post by covert on 2010-03-29
Some more info. Ubuntu does not seem to recognize it is gigabit capable.
```
#sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```

```
#lspic|grep Ethernet
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
```

---

