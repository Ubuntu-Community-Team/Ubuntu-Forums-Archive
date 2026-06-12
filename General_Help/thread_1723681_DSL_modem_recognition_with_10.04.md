---
title: "DSL modem recognition with 10.04"
date: 2011-04-07
forum: General Help
---

### Post by Gen Vert on 2011-04-07
Just fitted my netbook (Acer Aspire One) with 10.04 and now trying to connect to DSL Internet with Ethernet cable through Siemens 4200 modem.

The "Ethernet" light on the modem does not come on as it does when i'm in Windows on the netbook nor as it does when I connect my desktop (with an earlier version of 10.04 with no wireless capability). 

I've run out of things to try. 

Without that light on, don't think I can advance.

---

### Post by jerome1232 on 2011-04-07
Sounds like perhaps the ethernet port isn't being recognized by Ubuntu.

With the thing plugged in what is the output of these commands?

```
ifconfig
lshw -C network
```

---

### Post by Gen Vert on 2011-04-07
> **jerome1232 said:**
> Sounds like perhaps the ethernet port isn't being recognized by Ubuntu.

With the thing plugged in what is the output of these commands?

```
ifconfig
lshw -C network
```

Here are the results:

                     p { margin-bottom: 0.21cm; }  john@john-laptop:~$ ifconfig  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:72 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:72 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:05:68:ad   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 john@john-laptop:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network UNCLAIMED      
        description: Ethernet controller  
        product: AR8152 v1.1 Fast Ethernet  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: c1  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0  
        resources: memory:57000000-5703ffff ioport:5000(size=128)  
   *-network  
        description: Wireless interface  
        product: AR9285 Wireless Network Adapter (PCI-Express)  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 01  
        serial: 88:9f:fa:05:68:ad  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:17 memory:56000000-5600ffff 



What do they tell you!

---

### Post by jerome1232 on 2011-04-07
It tells me your ethernet controller is an Arhteros AR8152 which doesn't work out of the box with Ubuntu.

Searching google got me a few results with ways to get it to work, I found this how to on the ubuntu community help

[https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne/AOD250#Enabling%20wired%20network](https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne/AOD250#Enabling%20wired%20network)

It looks out of date should still should be helpful.

You'll need to download the linux driver for that card and compile it.

This is the driver page [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

You need a way to get that computer connected to the internet though, maybe through it's wireless nic at a hotspot, and install the build-essential package so you can compile.

---

### Post by Gen Vert on 2011-04-10
Thank you jerome 1232, now working 100%!

---

### Post by Gen Vert on 2011-05-05
The problem is back :sad: after downloading 105 recommended Ubuntu updates!
Here are the results for* ifconfig* and [I]lshw -C network.

[/I]                      p { margin-bottom: 0.21cm; }  john@john-laptop:~$ ifconfig  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:05:68:ad   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 john@john-laptop:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network UNCLAIMED      
        description: Ethernet controller  
        product: AR8152 v1.1 Fast Ethernet  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: c1  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0  
        resources: memory:57000000-5703ffff ioport:5000(size=128  
   *-network  
        description: Wireless interface  
        product: AR9285 Wireless Network Adapter (PCI-Express)  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 01  
        serial: 88:9f:fa:05:68:ad  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:17 memory:56000000-5600ffff

---

### Post by jerome1232 on 2011-05-05
You probably had a kernel upgrade, you just need to recompile and reinstall it (meaning the network adapter driver).

Not fun I know. Just be aware of it when you get kernel upgrades.

---

