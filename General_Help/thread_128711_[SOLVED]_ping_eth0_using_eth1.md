---
title: "[SOLVED] ping eth0 using eth1 ?"
date: 2006-02-12
forum: General Help
---

### Post by nuttycat on 2006-02-12
hi all,
Is there any way I can ping my eth0 interface using the eth1 interface?
(hope this is the correct place to post this)

I have two Ethernet interfaces:
eth0 : 192.168.10.1
eth1: 192.168.10.2

Is there anyway I can make a ping go from eth1 to eth0, prefereably externally using a crossover cable or similar cable (no hubs or other netwrking devices)

For a project I am working on, i need to be able to selectively read from eth0 or eth1 depending on some factors. 

This is still in the beginning stages so at this point I need to be able to check whether I am reading properly from either of the two interfaces.

I am doing most of this development on my home pc where I do not have a LAN. At the project place has a network and multiple machines, so its not a problem to check there, but at home it is.

Any pointers anyone?
Thanks,
Nuttycat

---

### Post by heimo on 2006-02-12
man ping was friendly and helped to find flag -I:
```
ping -Ieth0 [address]
```

---

### Post by nuttycat on 2006-02-12
Thanks heimo,
but unfortunately that did not work.

here's my ifconfig dump
```

suneil@Family:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:48:34:AE:FF
          [COLOR="Blue"]inet addr:192.168.10.1[/COLOR]  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fe34:aeff/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x1000

eth1      Link encap:Ethernet  HWaddr 00:00:E8:12:17:11
          [COLOR="Blue"]inet addr:192.168.10.2[/COLOR]  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe12:1711/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1308 (1.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2573441 (2.4 MiB)  TX bytes:2573441 (2.4 MiB)

```

but then when i put
```

ping -Ieth0 192.168.10.2

```

i get this 
```

suneil@Family:~$ ping -Ieth0 192.168.10.2
PING [COLOR="Blue"]192.168.10.2 (192.168.10.2) from 192.168.10.2 eth0:[/COLOR] 56(84) bytes of data.
From 192.168.10.1 icmp_seq=2 Destination Host Unreachable
From 192.168.10.1 icmp_seq=3 Destination Host Unreachable
From 192.168.10.1 icmp_seq=4 Destination Host Unreachable

--- 192.168.10.2 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4000ms
, pipe 3

```

if you look at the above you'll see that for some reason (unknown to me), its resolved eth0 as 192.168.10.2 , where as from the ifconfig it shows as clearly set to 192.168.10.1

any pointers?
Thanks,
Nuttycat

---

### Post by heimo on 2006-02-12
Nope, I think it shows what it should (other than that it's not responding to ping). You're trying to ping the x.x.x.2-address (on interface eth1), using interface eth0 (which has been assigned to address x.x.x.1).

I haven't done such test as you're (and am too tired at the moment to think how it should be done correctly), but I'd check routing:
```
route -n
``` 
:-k So you're putting two interfaces on same computer with addresses in same subnet... And connecting cards with crossover cable. (*checks behind computer*) I don't have two NICs at the moment, would have tried it otherwise. I'd guess that it's something like that you need to configure specific routes for each interface/address to achieve what you're trying. (Someone smarter than me will hopefully give you better instructions / correct answer.) It's normal to put two network cards in one computer, but in most cases those are in different subnets.

---

### Post by heimo on 2006-02-12
Maybe... Just maybe... (your setup is a bit "exotic")

You could try something like this:
```
sudo route add -host 192.168.10.2 eth0
sudo route add -host 192.168.10.1 eth1
```

---

### Post by nuttycat on 2006-02-12
thanks heimo,
I'll try that and get back.
-Nuttycat

---

### Post by nuttycat on 2006-02-20
Sorry it took so long to reply, 
but this has still not got sorted out.

heimo,
I took your suggestion of different subnets and did this
```

sudo route add -host 192.168.11.2 eth0
sudo route add -host 192.168.10.1 eth1

```

and then verified the routing table using this 
```

user@domain:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.2    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.10.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0        192.168.10.1        0.0.0.0         UG    0      0        0 eth0

```

then PING  gives this
```

user@domain:~$ ping 192.168.11.2
PING 192.168.11.2 (192.168.11.2) 56(84) bytes of data.
64 bytes from 192.168.11.2: icmp_seq=1 ttl=64 time=0.112 ms
64 bytes from 192.168.11.2: icmp_seq=2 ttl=64 time=0.093 ms
64 bytes from 192.168.11.2: icmp_seq=3 ttl=64 time=0.102 ms
64 bytes from 192.168.11.2: icmp_seq=4 ttl=64 time=0.094 ms
64 bytes from 192.168.11.2: icmp_seq=5 ttl=64 time=0.098 ms
64 bytes from 192.168.11.2: icmp_seq=6 ttl=64 time=0.094 ms
64 bytes from 192.168.11.2: icmp_seq=7 ttl=64 time=0.102 ms
64 bytes from 192.168.11.2: icmp_seq=8 ttl=64 time=0.076 ms
64 bytes from 192.168.11.2: icmp_seq=9 ttl=64 time=0.102 ms

```
so everything is great ? :-k 
unfortunately no, :confused: 

see what i get on a tcpdump request (on another terminal screen in the background)

```

user@domain:~$ sudo tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel

```

any ideas? now it seems to be doing the PING internally...How do I get it to go thru the cable? Please help !!

Thanks,
Nuttycat

ps: Am not sure if this is significant, but when the two interfaces are connected, the "link" leds do NOT glow, as they usually would if the network interfaces are connected to the regular network. Is is significant?

---

### Post by nanotube on 2006-02-20
maybe your "crossover" cable is not really a crossover cable, if you are not getting the link?

---

### Post by nuttycat on 2006-02-21
[QUOTE=nanotube]maybe your "crossover" cable is not really a crossover cable, if you are not getting the link?[/QUOTE]
that's an interesting thought... Its not a direct patch cable, i checked that with my DSL modem and the network card. Is there anyway to test it (for being a crossover cable), other than physically linking two PCs together? 

When i bought the cable, the shop guy assured me that it was a crossover. The shop guy only has one machine, so can't test there either.

anyother ideas?
Thanks,
Nuttycat

---

### Post by Revolution on 2006-02-21
Look at the connectors.

If the wiring is different then they are crossovers.

---

### Post by nanotube on 2006-02-21
well, hooking up two pcs together is the easiest... but you could also check the colors of the little wires in the connectors. (check online for proper arrangement of a crossover cable).

---

### Post by dcstar on 2006-02-22
[QUOTE=nuttycat]that's an interesting thought... Its not a direct patch cable, i checked that with my DSL modem and the network card. Is there anyway to test it (for being a crossover cable), other than physically linking two PCs together?
.......[/QUOTE]
If you have two configured LAN cards, plug the cable into them.

If the lights come on as with a normal connection, then you have the right cable, if there are no lights then either the cable is wrong - or one of the LAN interfaces isn't working.

---

### Post by nuttycat on 2007-09-29
I know this is a long time to respond to this thread.
I eventually traced down the bug to a partially faulty NIC card on one of the machines.
Thanks for all the input.

---

### Post by nanotube on 2007-09-29
> **nuttycat said:**
> I know this is a long time to respond to this thread.
I eventually traced down the bug to a partially faulty NIC card on one of the machines.
Thanks for all the input.

thanks for following up! someone somewhere at some point will find this helpful. :)

---

