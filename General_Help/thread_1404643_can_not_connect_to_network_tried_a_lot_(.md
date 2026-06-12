---
title: "can not connect to network tried a lot :("
date: 2010-02-11
forum: General Help
---

### Post by dragonair on 2010-02-11
hi, its my first post here on ubuntu :)

i just installed ubuntu 8.10 on my pc . before was xp installed. i formated the system and installed ubuntu . installation was successfull.

problem is that i cant connect to network . :( i know same thing have already been happened to others but. i could not figure out their replies as m a noob  :). 

my network card : realtek 8139 ethernet card

on ifconfig i get :

```

eth0      Link encap:Ethernet  HWaddr 00:16:76:af:23:b3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31896 (31.8 KB)  TX bytes:31896 (31.8 KB)

```also the connection is wired one with modem only it's reliance broadband.
the wire is connected between modem and pc  but there is no blinking of light for this connection . the wan is active and wan's light is blinking and when i was on xp on same pc there was no such problem :). 

please help ..reply asap : ^_^:p:D

---

### Post by Iowan on 2010-02-11
Post results (from a terminal) of **sudo lshw -C network**

---

### Post by dragonair on 2010-02-12
herez what i got on executing the coomand u said :)

```

sudo lshw -C network
---------------------

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:16:76:af:23:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:4d:0a:35:27:65
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



```

---

### Post by dragonair on 2010-02-12
please anyone ?? :(

---

### Post by dragonair on 2010-02-13
hi , pob got resolved .. :) .. today it got connected automatically :P hehe

---

