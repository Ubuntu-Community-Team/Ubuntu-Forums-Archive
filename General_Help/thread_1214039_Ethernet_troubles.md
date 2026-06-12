---
title: "Ethernet troubles"
date: 2009-07-15
forum: General Help
---

### Post by Java Geek on 2009-07-15
Hello, I run kubuntu 9.04 and my knetworkmanager was purged from the system. However, I plugged in my modem directly and linux is still not recognizing it. When I type: 
```

sudo lshw -C network
```

I get this result 
```

  *-network:0 DISABLED                         
       description: Ethernet interface         
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek                                        
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:89:9e:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:e8:71:a9
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.55+,07/23/2007,6.0.3.107 latency=128 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:15:c7:5a:c1:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Please help me enable my ethernet so that I can at least do something about the rest of my system... BTW, I have modem only for another hour or so tops.

---

### Post by Kraut~salat on 2009-07-15
just because knetworkmanager was purged doesn't keep you from simply reinstalling it.

Secondly have you tried simple measures such as

ifconfig <what ever name your interface has> up

?

---

### Post by c0mput3r_n3rD on 2009-07-15
Try taking out the ethernet plug, turn off the computer, turn it back on, wait until it finishes loading, and plugging in the ethernet cable.  Sometimes that's what I have to do.

Note: Do not just restart, fully shutdown, and boot it back up after HDD stops spinning.

---

### Post by Java Geek on 2009-07-15
> **c0mput3r_n3rD said:**
> Try taking out the ethernet plug, turn off the computer, turn it back on, wait until it finishes loading, and plugging in the ethernet cable.  Sometimes that's what I have to do.

Note: Do not just restart, fully shutdown, and boot it back up after HDD stops spinning.

Thanks, I'll give it a shot!

---

### Post by Java Geek on 2009-07-15
> **Kraut~salat said:**
> just because knetworkmanager was purged doesn't keep you from simply reinstalling it.

Secondly have you tried simple measures such as

ifconfig <what ever name your interface has> up

?

yes...Thats the issue...Its not working that way.

---

### Post by Java Geek on 2009-07-15
Neither of the above suggestions worked =(

What's really weird is that my computer shows internet activity when it is stating that there is no internet. I just need to run apt!

---

