---
title: "network pppoeconf problem?"
date: 2009-10-07
forum: General Help
---

### Post by abhilashm86 on 2009-10-07
i've a DSL modem, since my internet was low, i tried sudo pppoeconf in terminal, just after that it asked series of username and password,

now internet is working, but i'm getting a unique local ip address, my default mostly is 192.168.1.2, also internet connection is switching on and off............

```
abhilash@abhi:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:54:ba:81:45  
          inet6 addr: fe80::223:54ff:feba:8145/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22317296 (22.3 MB)  TX bytes:3991555 (3.9 MB)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119276 (119.2 KB)  TX bytes:119276 (119.2 KB)

pan0      Link encap:Ethernet  HWaddr a2:19:59:a3:42:3c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.192.119.38  P-t-P:117.192.112.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:1491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1430372 (1.4 MB)  TX bytes:140051 (140.0 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
why did ip address changed drastically? first time i'm seeing this ip from 2 years!!
i want to disable pppoeconf, how to do it?? help please

---

### Post by mr.suchy on 2009-10-07
maybe this will help You

[http://ubuntuforums.org/showthread.php?t=1153758]("http://ubuntuforums.org/showthread.php?t=1153758")

---

### Post by abhilashm86 on 2009-10-07
right now pppoeconf has crashed my system witjout any access to internet,
pppoeconf strangely detected some random ip 10.23.15.02 (something i wont remember), then even my isp page was also not opening..........
then i tried going and disabling pppoeconf,
after reboot everything of network is meesed up, even if i manually configure network, its not taking!! 
went to /etc/init.d, disabled auto pppoeconf, hmm i need to see wil my network corrects.........replying from live cd 9.04!!

---

### Post by abhilashm86 on 2009-10-07
today is best day of my life with ubuntu!! i'm fully happy..........
linux just rocks!! with source code editing:) i won today..........

internet was not connecting with modem, pppoeconf had given some random ip, 
my ISP don't know linux, he knows just windows and i don't have windows!!

i thought i failed and need to re-install ubuntu..........
i got frustated and browsed all network files just to stop pppoeconf , but in vain, then i went to /etc/init.d and stoped it from auto during booting........

then came back to forums, saw link of thread and followed details, i won billion bugs!! forums just rocks, keep it on people, hava a gr8 day!!:)

---

### Post by abhilashm86 on 2009-10-07
> **mr.suchy said:**
> maybe this will help You

[http://ubuntuforums.org/showthread.php?t=1153758]("http://ubuntuforums.org/showthread.php?t=1153758")

thanks a ton friend, u saved my day:)

---

