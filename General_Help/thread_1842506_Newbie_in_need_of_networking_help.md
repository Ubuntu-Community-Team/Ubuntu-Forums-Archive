---
title: "Newbie in need of networking help"
date: 2011-09-11
forum: General Help
---

### Post by Jiggle156 on 2011-09-11
I recently got fed up with windows 7, and thought to myself - right. Time for a change. So I stuck Ubuntu 11.04 on my USB stick, and booted from it directly to test it out. 

It does not detect my wired network at all, but my installation of windows 7 does.

Being a complete newbie to Linux, and networking in general - could someone please help me out? Really want to get started with Ubuntu :(

---

### Post by TeoBigusGeekus on 2011-09-11
Can you post us the output of
```
ifconfig
```
and
```
lshw -C network
```
?

---

### Post by Jiggle156 on 2011-09-11
How would I do that?
I have to restart the computer to boot ubuntu from my flash drive, then back again to boot Win7. Is there a workaround?

---

### Post by TeoBigusGeekus on 2011-09-11
I don't think so.

You have to boot into ubuntu, open a terminal, issue the commands I gave you, copy and paste their output into a text file, save the text file somewhere in your windows partition and then boot windows and post us its contents.

---

### Post by Jiggle156 on 2011-09-11
ifconfig:

```



eth0      Link encap:Ethernet  HWaddr 70:5a:b6:d2:8a:89  
          inet6 addr: fe80::725a:b6ff:fed2:8a89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:4252 (4.2 KB)  TX bytes:7367 (7.3 KB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr c4:17:fe:c0:4c:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lshw -C network (Not as Super-User)

```

*-network               
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:c0:4c:9b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d4100000-d4103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:d2:8a:89
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:d3000000-d303ffff ioport:1000(size=128)

```

---

### Post by TeoBigusGeekus on 2011-09-11
Both your ethernet and your wireless chip are detected and reported with a working driver.
Do you have at least wireless?
If yes, you can run the update manager to see if the updates correct your problem.

---

### Post by Jiggle156 on 2011-09-11
I haven't tried it, generally speaking I am opposed to the use of wireless internet. Once connected, how do I get the updates?

---

### Post by TeoBigusGeekus on 2011-09-11
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Jiggle156 on 2011-09-11
I run both of them, one after the other?

---

### Post by drdos2006 on 2011-09-11
And could I also ask, can you type "ping 8.8.8.8" from a terminal and tell us what the result is ?

regards

---

### Post by TeoBigusGeekus on 2011-09-11
> **Jiggle156 said:**
> I run both of them, one after the other?

Yeap.

---

### Post by Jiggle156 on 2011-09-11
Right-

I connected to the Internet wirelessly, and started the update - but I lack the space on my USB to complete the update. I put all of the relevant information into the network settings for my wired connection, but it still doesn't work. The network is detected, and the two arrows appear in the top right of the screen. But it does not connect to the internet.

---

### Post by Jiggle156 on 2011-09-12
Bump for assistance.

---

### Post by Jiggle156 on 2011-09-12
Think I have resolved the problem, by manually inputting my network info.

---

