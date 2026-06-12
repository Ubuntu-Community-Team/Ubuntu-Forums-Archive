---
title: "Wireless Card stopped finding network (10.10)"
date: 2011-05-08
forum: General Help
---

### Post by malenkylizards on 2011-05-08
My girlfriend's desktop has been running Ubuntu 10.10 just fine since December.  Today, the connections menu shows nothing but "Wireless Networks: disconnected."  My laptop is inches away and has a full connection.

I'm not sure what diagnostic tools I have at my disposal.  The one thing I've been able to do is lspci.  The relevant output of sudo lspci -v | less is:
03:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
Subsystem: RaLink EW-7108PCg
Flags: bus master, slow devsel, latency 64, IRQ 20
Memory at febf8000 (32-bit, non-prefetchable) [size=32K]
Capabilities: [40] Power Management version 2
Kernel driver in use: rt61pci
Kernel modules: rt61pci

What's the next step?

---

### Post by matt_symes on 2011-05-08
Hi

Open up a terminal and post the output of these two commands

```
cat /var/lib/NetworkManager/NetworkManager.state
service network-manager status
```

It's case sensitive so the best way is to copy and paste it into a terminal and the output from the terminal

Kind regards

---

### Post by malenkylizards on 2011-05-16
cat /var/lib/NetworkManager/NetworkManager.state yields the following output:

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true


and service network-manager status:
network-manager start/running, process 904

Sorry about the week delay!  Finals happened.  I guess I posted prematurely earlier, but I'm ready to work on this problem now.  So most obviously, WirelessEnabled is false.  How do I fix this?

---

### Post by malenkylizards on 2011-05-16
Oops, I googled.  I sudo nano'd the file to make false = true, and restarted the computer.  That fixed it.  Can't be sure yet if it's a temporary fix, since I'm not sure why it happened in the first place, but for now it works!

---

