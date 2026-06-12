---
title: "No Internet despite Network Card Detection"
date: 2006-04-04
forum: General Help
---

### Post by raja.aydina on 2006-04-04
Hi! I'm new to ubuntu and linux in general. The problem i'm facing with is that there is no network connection.  The connection is split with a router to a ubuntu 5.10 desktop and my laptop with dd6.06 ( i had the same problem when  i had 5.10 on) (Travelmate 630, Realtek Network Card (i dont know the exact number of the top of my head but i can look it up)).  The internet works fine for the desktop but for the laptop despite detecting the network card, with lights flashing etc.. I still get no internet. Help!

---

### Post by jamesr on 2006-04-04
post the outputs of```
sudo ifconfig -a
sudo iwconfig -a
cat /etc/resolv.conf
```

---

### Post by raja.aydina on 2006-04-05
eth0      Link encap:Ethernet  HWaddr 00:00:E2:7E:AF:C3
          inet6 addr: fe80::200:e2ff:fe7e:afc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:132214 (129.1 KiB)  TX bytes:2178 (2.1 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



sudo iwconfig -a
-a        No such device


cat...
nameserver 24.92.226.9
nameserver 24.92.226.102

---

### Post by _linux_ on 2006-04-05
I have a similar (maybe even the same) problem. It detected the wireless card and the Internet worked. Then the second time, the network, signal, etc. was working, but I couldn't go to any sites. Very weird. Hopefully, there's a solution.

---

### Post by jamesr on 2006-04-05
It is seeing the NIC as eth0 and the resolv.conf looks oK

```
sudo dhclient
``` Also try and ping the router.

---

### Post by raja.aydina on 2006-04-05
Thanks for your help.  At the end of "sudo dhclient" I get "No DHCPOFFERS recieved." I tried to ping the router too, (i'm not sure if this is the code but i used "sudo ping IP number" and it told me "connetc: Network is unreachable." Can you think of any other possibilities? Thanks again

Aydina

---

