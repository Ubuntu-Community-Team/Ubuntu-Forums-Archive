---
title: "Internet connection too slow.."
date: 2010-03-02
forum: General Help
---

### Post by karthick87 on 2010-03-02
My internet connection is too slow..Sometimes it doesn't receive any packets..What may be the problem?

```
karthick@Learners-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:17:70  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:feab:1770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3045488 (3.0 MB)  TX bytes:678940 (678.9 KB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4348194 (4.3 MB)  TX bytes:4348194 (4.3 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.92.115.7  P-t-P:59.92.112.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2959233 (2.9 MB)  TX bytes:595647 (595.6 KB)
```

---

### Post by emanuel.b on 2010-03-02
Same thing here, download speed is unaffected, but sometimes connections to websites are dropped or ignored. Can any one help? :confused:

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d4:36:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3264 (3.2 KB)  TX bytes:3264 (3.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:1e:d9:10  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe1e:d910/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14794430 (14.7 MB)  TX bytes:5156382 (5.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-1E-D9-10-31-65-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by efflandt on 2010-03-02
**getyourkarthick** what kind of DSL modem do you have, and I am curious if it is really a bridge modem (or in bridge mode) or is it really a modem/router.  What assigned an IP to eth0 and is that just to access your modem itself (does it show sync speed or have statistics) or is your modem doing pppoe and you are trying to do pppoe on your PC too.  Do you have to do PPPoE on your PC in Windows?

The output of **route -n** may reveal something.  You should only have one default gateway (to the internet).

**emanuel.b** you could any number of issues related to wireless, link quality, interference from 2.4 GHz cordless phone, a strong neighbor on the same channel, your internet connection itself.  If you have SSID broadcast disabled on your wireless router, that can slow you up (your PC cannot tell if your AP is still up without chatting with it), and does not really help security any (SSID is revealed in any traffic).

-- 

I have a nic on an old PC that I have to force back to 10baseT, because otherwise it sometimes goes into a frenzy trying to autonegotiate speed with some devices, resulting in 25-50% packet loss.  Although, it works fine at 10baseT full-duplex.

---

### Post by karthick87 on 2010-03-03
```
karthick@Learners-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.92.112.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

---

