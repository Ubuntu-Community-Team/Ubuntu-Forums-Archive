---
title: "Incorrect MAC address in 9.10"
date: 2009-11-03
forum: General Help
---

### Post by subiet on 2009-11-03
Here is the problem and what I have tried till now:

The problem:

Can't connect to wired LAN (auto eth0)

It used to work in jaunty.

What all have i tried:

1) LAN works on win7, so hardware is fine.

2) used the same live cd on a different machine and it connects.

Then I checked my mac address in windows and in linux (network manager > edit connections > edit auto eth0) and it shows a different one than windows one. 

below is the output of lshw -c network

```
 *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:57:14:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:19 memory:fd5fcc00-fd5fcc7f ioport:cc00(size=128)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:6f:51:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=10.2.3.11 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fd7f0000-fd7fffff

```

---

### Post by pedro_orange on 2009-11-03
> **subiet said:**
> Here is the problem and what I have tried till now:

The problem:

Can't connect to wired LAN (auto eth0)

It used to work in jaunty.

What all have i tried:

1) LAN works on win7, so hardware is fine.

2) used the same live cd on a different machine and it connects.

Then I checked my mac address in windows and in linux (network manager > edit connections > edit auto eth0) and it shows a different one than windows one. 

below is the output of lshw -c network

```
 *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:57:14:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:19 memory:fd5fcc00-fd5fcc7f ioport:cc00(size=128)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:6f:51:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=10.2.3.11 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fd7f0000-fd7fffff

```

Thats very strange. 

Can you please give some more information regarding the network? Is it all setup to DHCP? Are there any restrictions set on the router to only allow certain MAC Addresses etc to connect? 
Do you have the wireless card connected at the time you are trying to connect the eth0 up?

I've found wired connections to be solid on Ubuntu. Literally just plug it into a DHCP router and you're away.

---

### Post by subiet on 2009-11-03
Ok, now it shows the correct mac address also.

But i still can't connect, either via DHCP or via Static IP

---

### Post by P4man on 2009-11-03
I read about a bug with dhcp which had a simple workaround which I forgot. Perhaps it was settings the connection "available to all users" ? Dont remember, but it cant hurt trying.

If that fails, i suggest you install wcid and remove gnome network manager

---

### Post by subiet on 2009-11-03
have tried wicd too, no help. tried config files too, no help.

---

### Post by P4man on 2009-11-03
But did you try this:
[IMG]http://img29.imageshack.us/img29/4827/screenshot001yj.png[/IMG]

---

### Post by subiet on 2009-11-03
yepp tried both ways, checked and unchecked on "dhcp" and "static"

---

### Post by pedro_orange on 2009-11-03
Can you run an ifconfig?

If you set your IP to static (within the correct range for your router) can you ping your router?

Is your wireless connection enabled?

---

### Post by subiet on 2009-11-03
no i can't ping router after manually setting the ip, though it shows that connected to auto eth0, but i am not really on the network.

tried with wireless on and off. Wireless in general is working perfect

---

### Post by pedro_orange on 2009-11-03
[DHCP]
Terminal:

```
ifconfig
```

Post it here.

[Change it to Static]
What is the IP Address of your router?
What IP Address and Subnet are you giving your eth0?

Terminal
```
ifconfig
```

Post it here.

(Make sure the wireless card is OFF for the whole process)

---

