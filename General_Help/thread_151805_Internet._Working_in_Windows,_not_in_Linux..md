---
title: "Internet. Working in Windows, not in Linux."
date: 2006-03-28
forum: General Help
---

### Post by linux_owns on 2006-03-28
Hey,
I've been on ubuntu for about 3 weeks and have loved it. I'm on Ubuntu breezy, but today I cant get either eth1 or eth0 to work. When i boot up to windows both work fine. Back to linux, i type sudo dhclient eith1, or sudo /etc.init.d/networking restart... but neither of those do anything. I've been reading in the foroms and i cant seem to get anythign to work. i've also tried dhclient -r and something else that i read.

both are detected and seem to be working, but when i try to do anything like go on the web, i get no responce.

Please help. 
 this is my ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:01:4A:5D:63:65
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:fe5d:6365/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10066 (9.8 KiB)  TX bytes:11132 (10.8 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:212685 (207.7 KiB)  TX bytes:212685 (207.7 KiB)

---

### Post by m0ther on 2006-03-28
hello - i had a similar problem - the solution eventually was to mkae a change to one of the firefox settings. maybe give it a whirl;

type **about:config** in the address bar

find the section called **network.dns.disableIPv6**

set the value to true

that solved it for me (although i now don't need that setting - possibly a fix in v 1.5..?)

good luck - that annoyed me for a long time :-?

---

### Post by linux_owns on 2006-03-28
Thanks, still not working. 
I can ping but its very slow.
I'm on dsl.
Anybody have suggestions?
thanks.

---

### Post by linux_owns on 2006-03-28
Thanks alot!
you tipped me off with that ipv6! once i disabled that in my settings (/etc/modporbe.d/aliases) and in firefox, it works!
your the man!

---

