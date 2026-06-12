---
title: "Cannot connect to the internet after installing Ubuntu 8"
date: 2009-07-14
forum: General Help
---

### Post by jasdar on 2009-07-14
Hi everyone,
 
I am new to this, so please forgive my ignorance. I just installed a version of Ubuntu on my desktop (dual boot, within Windows XP Professional), and for some reason I cannot connect to the internet through Ubuntu.
 
I can however, connect to the internet using my XP install.
I have a home network, connected to a modem, with each pc on the -
10.x.x.x, 255.255.255.0 network.The default gateway is 10.1.1.1.
I can ping my own address - 10.1.1.6 and the loopback address. However I am unable to ping the another PC (on the same network) with the IP address 10.1.1.5.
 
I have configured the IP address to a static one and this is what I get when I type an ifconfig on a terminal window.
 
eth0 Link encap:Ethernet HWaddr 00:1f:c6:85:fc:f3 
inet addr:10.1.1.6 Bcast:10.1.1.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Memory:dffc0000-e0000000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:88 errors:0 dropped:0 overruns:0 frame:0
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:5516 (5.3 KB) TX bytes:5516 (5.3 KB)
 
 
The file /etc/hosts contains the following - 
127.0.0.1 localhost
127.0.1.1 ourhome-desktop
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
 
I have tried by commenting out the ipv6 addresses and then trying to connect but to no avail unfortunately. I have gone through some forum threads and tried various things, but still no luck...:(
 
Is anyone please able to help???
 
Thanks in advance!!
 
-Jas

---

### Post by Sef on 2009-07-14
Are you using 8.04 or 8.10?

---

### Post by jasdar on 2009-07-14
Ubuntu - 8.04.1

Thanks...

---

