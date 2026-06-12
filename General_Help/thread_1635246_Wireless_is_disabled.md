---
title: "Wireless is disabled"
date: 2010-12-01
forum: General Help
---

### Post by ChaosChris2009 on 2010-12-01
[CENTER]Hello, when I boot into Xubuntu 10.10 32-Bit

I have a laptop running Windows 7 Ultimate 32-Bit, the wireless works just fine, the laptop has a built wirless card

there's always 2 arrows where the wireless icon is, it says

wireless is disabled

and if I enable wireless it says

device is not ready

How can I get the wi-fi to work on my laptop in Xubuntu 10.10?

I ran these commands and this is what gave me

```
dmesg grep -i net
```

```
c@ubuntu:~$ dmesg | grep -i net
[    0.004327] Initializing cgroup subsys net_cls
[    0.157208] NET: Registered protocol family 16
[    0.229545] NetLabel: Initializing
[    0.229547] NetLabel:  domain hash size = 128
[    0.229549] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.229564] NetLabel:  unlabeled traffic allowed by default
[    0.288670] NET: Registered protocol family 2
[    0.290181] NET: Registered protocol family 1
[    0.291550] audit: initializing netlink socket (disabled)
[    0.576746] NET: Registered protocol family 10
[    0.577467] NET: Registered protocol family 17
[    0.899023] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   17.299499] type=1400 audit(1291238770.185:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   19.219483] type=1400 audit(1291238772.105:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=899 comm="apparmor_parser"
[   19.566445] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

```
ifconfig -a
```

```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:6e:89:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6896 (6.8 KB)  TX bytes:6896 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:aa:0f:3f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```[/CENTER]

---

### Post by ChaosChris2009 on 2010-12-01
Bump for possible solution

---

### Post by BigCityCat on 2010-12-01
right click on the network icon in the panel and check enable wireless.

---

### Post by ChaosChris2009 on 2010-12-01
> **BigCityCat said:**
> right click on the network icon in the panel and check enable wireless.

I did, still doesn't work

It says device not ready

---

### Post by t4thfavor on 2010-12-01
Boot windows, turn it on, then boot linux, and try it. 

Device not ready could also just mean that it isn't connected which really isn't a problem (just figure out how to connect).

---

### Post by ChaosChris2009 on 2010-12-01
> **t4thfavor said:**
> Boot windows, turn it on, then boot linux, and try it. 

Device not ready could also just mean that it isn't connected which really isn't a problem (just figure out how to connect).

Still turns out the same no matter how many times I boot into the Linux partition

---

### Post by 0949er on 2010-12-01
is the car supported? how old is the laptop? (assuming its fairly new if it has windows 7 on it... or new enough to have wireless support in linux)

has it ever worked? what model is the network card?

---

### Post by ChaosChris2009 on 2010-12-01
> **0949er said:**
> is the car supported? how old is the laptop? (assuming its fairly new if it has windows 7 on it... or new enough to have wireless support in linux)

has it ever worked? what model is the network card?

It's worked before with previous and older versions of Ubuntu Linux and other distros, I just don't why it suddenly stopped working in 10.10

Laptop is about 3 years old

---

### Post by ChaosChris2009 on 2010-12-05
Help me please

---

### Post by piquat on 2010-12-06
After a fresh install, after installing drivers and then turning it on... that's where it leaves me... "device not ready".

At that point I right click the connection applet and choose "Edit Connections" to create a wireless connection.  Maybe you lost the setup for it or it got corrupted.  Have you tried deleting it (the connection) and setting it up again?

---

