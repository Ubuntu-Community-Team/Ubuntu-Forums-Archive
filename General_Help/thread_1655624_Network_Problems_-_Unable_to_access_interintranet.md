---
title: "Network Problems - Unable to access inter/intranet"
date: 2010-12-29
forum: General Help
---

### Post by tsukasa_kun on 2010-12-29
Hello all~

I've recently installed Ubuntu server 10.10 on an older Pentium 3 computer to test the capabilities of Ubuntu and to have more experience with the OS.

During my install, the network card, a Kingston KNE100TX, was successfully detected however auto configuration failed. This was tried against a Windows 2k3 DHCP server as well as a Cradlepoint router. As expected, since no DHCP server provided an address, the routing table is empty.

I retried configuring the Kingston card with a static IP address. This time as expected, ifconfig showed the IP address that was assigned and the route table had been populated. Attempting to ping my gateway, 192.168.17.1, resulted in Destination Host Unreachable. The same results were encountered when the configuration was changed to a different network.

I've since replaced all cables, twice, and even swapped network cards in different PCI slots to no avail. Other computers on the network are unable to ping the Ubuntu computer. Other computers on the network are able to ping the gateway that the Ubuntu server cannot. There is no firewall running on the Ubuntu server.

I'm currently back using the Kingston card. Eth 0 is currently configured as:
```

iface eth0 inet static
  address 192.168.17.31
  netmask 255.255.255.0
  network 192.168.17.0
  broadcast 192.168.17.255
  gateway 192.168.17.1
  dns-nameservers 192.168.17.1
  dns-search federation.dmz

```The kernel reports the following for the network card:
```

description: Ethernet interface
product: DECchip 21142/43
vendor: Digital Equipment Corporation
physical id: 13
bus info: pci@0000:00:13.0
logical name: eth0
version: 41
serial: 00:c0:f0:4b:db:8d
width: 32 bits
clock: 33MHz
capabilities: bus_master rom ethernet physical
configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.17.31 latency=64 maxlatency=40 mingnt=20 multicast=yes
resources: irq:11 ioport:ec00(size=12) memory:fedbdfc00-febdfff memory:feb80000-febbfff

```Any suggestions on other things I can try? My end goal is to get at least apt-get running to upgrade/install linux features.

Thanks!
Tsukasa

---

### Post by dcstar on 2010-12-30
> **tsukasa_kun said:**
> Hello all~

I've recently installed Ubuntu server 10.10 on an older Pentium 3 computer to test the capabilities of Ubuntu and to have more experience with the OS.

During my install, the network card, a Kingston KNE100TX, was successfully detected however auto configuration failed. This was tried against a Windows 2k3 DHCP server as well as a Cradlepoint router. As expected, since no DHCP server provided an address, the routing table is empty.

I retried configuring the Kingston card with a static IP address. This time as expected, ifconfig showed the IP address that was assigned and the route table had been populated. Attempting to ping my gateway, 192.168.17.1, resulted in Destination Host Unreachable. The same results were encountered when the configuration was changed to a different network.

I've since replaced all cables, twice, and even swapped network cards in different PCI slots to no avail. Other computers on the network are unable to ping the Ubuntu computer. Other computers on the network are able to ping the gateway that the Ubuntu server cannot. There is no firewall running on the Ubuntu server.

I'm currently back using the Kingston card. Eth 0 is currently configured as:
The kernel reports the following for the network card:
Any suggestions on other things I can try? My end goal is to get at least apt-get running to upgrade/install linux features.

Thanks!
Tsukasa

[LIST=1]
[*]Do not "quote" data - use the Code tags.
[*]Install and use the **ethtool** package.
[*]Run **ifconfig** to see what is actually set up.
[/LIST]

---

### Post by robinmatthew on 2010-12-30
I am agree with David. As david said don't add qoute in your commands.
This is ubuntu not a windows...

---

### Post by tsukasa_kun on 2011-01-02
ifconfig eth0:
```

Link encap:Ethernet  HWaddr 00:c0:f0:4b:db:8d
inet addr:192.168.17.31  Bcast"192.168.17.255  Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:2 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:11 Base address:0xec00

```

When I do ethtool eth0, I get:
```

Settings for eth0:
No data available

```

What should I be getting for ethtool?

---

### Post by tsukasa_kun on 2011-01-08
Anyone? Thoughts? I'm running out of things to try to figure this out.

---

### Post by The Cog on 2011-01-08
That ifconfig is interesting. The fact that it says RUNNING means it has detected the cable and thinks the network is working.

The fact that both transmit and receive packets are zero is very significant. Two transmit errors might also be significant. I think you have problems with that NIC or its drivers. Beyond that, I don't know.

---

### Post by tsukasa_kun on 2011-01-09
I agree with that... I've tried a couple different brand network cards up to this point in all the different PCI slots on the board; all of which have the same results. I'm leaning more toward drivers at this point. What options do I have in dealing with what driver/card Ubuntu thinks I need to be using?

---

### Post by The Cog on 2011-01-09
That's odd. My only suggestion might have been to try using different brand PCI cards, and that's what you have done.

My only other thought is to try a recent live CD with the on-board network adapter and the other PCI ones, just in case something in your on-disk installation is borked.

---

### Post by loopduplicate on 2011-01-14
I am having the same problem on a fresh install.  Not sure what's up.

---

