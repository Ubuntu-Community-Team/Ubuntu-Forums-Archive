---
title: "Other machine cannot see ubuntu machine nor can it see it' self"
date: 2011-01-29
forum: General Help
---

### Post by Brian R. on 2011-01-29
Ubuntu 10.10 HELP HELP. I have 2 computers a laptop win 7 and a desk top Ubuntu, and up until today both could see and talk to each other. On the win 7 machine i turned password protected sharing ON to check that others could not see my shared folders when using public net works, then turned it back OFF and checked that ubuntu could still see and share the shared folders, which it could. But now nothing can see the ubuntu machine, nor can it see it's self when i click the network button (that's why i think it is a ubuntu problem and not a windows problem). eth0 had disappeared to be shown as wired 1. After much messing around i decided to re-install ubuntu (twice) and let it find every thing again, also installed win 7 to make sure the 2 computers could see each other. Then re-installed ubuntu for 3rd time. It still cannot see in's self nor can the other computer see it. eth0 is showing never used. Have changed IPV4 settings to manual,
Address 192.168.1.3  Netmask 255.255.255.0 Gateway 192.168.1.1 and the DNS to 192.168.1.1. There was nothing in the Mac address so dug around on the windows machine and saw it was using 00:27:19:cc:d6:b6 and used that, but did not put any thing in the Cloned Mac Address not sure what it is. supposed to be.I have found the networked printer and set it up with out problem, What has gone wrong.

---

### Post by Iowan on 2011-01-29
A couple of things to check from a terminal (Applications>Accessories>Terminal):
Does **ifconfig -a** confirm the adapter has an address?
Can the machine **ping** 192.168.1.1?

If this works - you can try **ping**ing the Win7 box by address.
If that is successful, then networking is fine - it's on to debugging filesharing...

---

### Post by Brian R. on 2011-01-29
Yes it can ping the modem router, and ping the other machine, it fails when i tries to ping it's self. More information, updates downloaded last night, and went back to network connections and saw that :Auto eth0" was still saying never accessed, but a new connection was listed as "Auto Ethernet" and had been accessed 1 Min. ago, still no solution to the problem. Whent back into connections deleted all and put in "Auto eth0" with Mac address shown in ifconfig, and left ipv4 settings as automatic (DHCP). Below is my ifconfig output.
bucky@bucky-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:5a:d3:82  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe5a:d382/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35459677 (35.4 MB)  TX bytes:4952134 (4.9 MB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

bucky@bucky-desktop:~$

---

### Post by Brian R. on 2011-01-29
SOLVED I went to share a folder and was told the necessary software was not installed, installed it and all is working as should be.

Thank you for pointing me in the right direction.

Brian R.

---

