---
title: "Internet keeps disconnecting after a while"
date: 2010-10-07
forum: General Help
---

### Post by failmerc on 2010-10-07
Hey people,

Help me out here I'm desperate after logging into Windows again (it's so crap :(), but I really have no choice cause my internet keeps disconnecting on Ubuntu after a while. Right now I'm on 10.10 Beta but this problem occured on 10.04 LTS as well (that's why I upgraded, hoping it would stop). 

I had this problem in Windows 7 as well and managed to fix it by using some program similar to Driver Doctor that locates all the drivers you need and don't have yet. It turned out to be a driver for some Adapter back then. 

However, I'm not aware of any of these programs designed for Linux and I don't know myself what Adapter drivers I need. 

Also, back in the day when I was using Ubuntu 9.10 I didn't have problems with internet disconnecting all the time. 

Anyone of you got any idea what's causing this? I hate being on Windows again. :(

---

### Post by lrgmmc on 2010-10-07
It would help to list the network adapter. is it wireless or not? what network manager are you running? all important questions that can help pthers help you.

---

### Post by failmerc on 2010-10-07
Not wireless...

VIA VT6102 Rhine II Fast Ethernet Adapter

If that's what you mean. :P

---

### Post by MooPi on 2010-10-07
Lets try a couple of commands in terminal and see what is revealed
```
sudo lshw -C network
```
```
ifconfig -a 
```
```
less /etc/network/interfaces
```
Post the results back here please.

---

### Post by failmerc on 2010-10-07
*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:1a:92:1d:3d:53
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half ip=192.168.2.103 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:9400(size=256) memory:dffff800-dffff8ff

eth0      Link encap:Ethernet  HWaddr 00:1a:92:1d:3d:53  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe1d:3d53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1635 errors:9 dropped:0 overruns:0 carrier:9
          collisions:2792 txqueuelen:1000 
          RX bytes:1531375 (1.5 MB)  TX bytes:315571 (315.5 KB)
          Interrupt:23 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5150 (5.1 KB)  TX bytes:5150 (5.1 KB)

auto lo
iface lo inet loopback

/etc/network/interfaces (END)

---

### Post by MooPi on 2010-10-07
Lets add some info to your /etc/network/interfaces
Start with ```
gksu gedit /etc/network/interfaces
```
Then add these lines 
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
``` Save and close.
For good measure in terminal ```
sudo ifup eth0
```
Hope that helps.

---

### Post by failmerc on 2010-10-07
I will set topic to solved for now. I'll report back if my internet disconnects again.

Thanks.

---

### Post by failmerc on 2010-10-08
> **failmerc said:**
> I will set topic to solved for now. I'll report back if my internet disconnects again.

Thanks.

Nope it didn't work too...

Strange, whenever I reboot internet just goes back on again.

---

### Post by MooPi on 2010-10-08
I noticed that your network card is running half dulex and may support full. Install this application ethtool
```
sudo apt-get install ethtool
```
Then run the app for your adapter
```
sudo ethtool eth0
```
Post the results back here.

---

### Post by failmerc on 2010-10-08
> **MooPi said:**
> I noticed that your network card is running half dulex and may support full. Install this application ethtool
```
sudo apt-get install ethtool
```Then run the app for your adapter
```
sudo ethtool eth0
```Post the results back here.

There ya go 

    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000001 (1)
    Link detected: yes

---

### Post by Quarkrad on 2010-10-08
I'm having this problem (with 10.04) with a wireless USB device.  Connection has been rock steady from Ubuntu 8.x and 9.x but keeps falling over with 10.04.  Had some good support on this site but so far no luck - strange how it always seems to disconnect just as you are paying for something on the net.  Good luck with your connection - perhaps I've had too much luck with Ubuntu so far and it is my turn to have something not working.

---

### Post by MooPi on 2010-10-08
Add this after your iface eth0 inet dhcp
```
pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full
```
If that doesn't work lets try turning auto negotiation off by adding ```
autoneg off
```

---

### Post by failmerc on 2010-10-09
> **MooPi said:**
> Add this after your iface eth0 inet dhcp
```
pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full
```If that doesn't work lets try turning auto negotiation off by adding ```
autoneg off
```

I'll wait with applying this, unless you advise me it (for speed or something, I don't know what it's for) cause my internet hasn't disconneted for 24 hours now.

---

