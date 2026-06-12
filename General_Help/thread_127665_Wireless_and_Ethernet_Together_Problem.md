---
title: "Wireless and Ethernet Together Problem"
date: 2006-02-09
forum: General Help
---

### Post by OPaul on 2006-02-09
If I boot my laptop up with just the Ethernet cable attached I have no problem. But then if I plug my wireless card in my Internet connection goes away completely, I can not ping any sites. I have to deactivate the Ethernet to get the wireless to work.  How can I get my Ethernet to either automatically deactivate when it sees the wireless connection is there or just work with both and pick one or the other?

---

### Post by jcl on 2006-02-09
Do they have separate IP addresses? Are they on separate subnets? If so, is your routing table correct (netstat -rn)? Can you ping the gateways on both interfaces?

---

### Post by OPaul on 2006-02-09
Different IP addresses, both provided via DHCP from the same router.. so yea, same subnet. 

```
Kernel IP routing table
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
 192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
 192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
 0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
 0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
```

I can ping the gateway, but nothing else. Not sure which interface it's using at this point though.

Basically I can't have both Ethernet and Wireless active at the same time, I can deactivate one of them and then everything is fine.

---

### Post by jcl on 2006-02-09
Hey OPaul,

I'm sure there is a way to do this, but I've never personally had two separate network interfaces on the same subnet. Post a copy of your 'ifconfig -a' output as well... Just so I understand, you have a hard wired connection and a wireless connection to a wireless router? Is there a reason why you want two interfaces on the same subnet? Is your nameserver different than your default gateway? Can you do an 'nslookup www.yahoo.com'? Can you do a traceroute to your nameserver from network tools?

---

### Post by AndyCooll on 2006-02-09
I had a problem similar to this when trying to get my wireless network to work properly. Essentially when booting up both my eth0 and rausb0 connections were conflicting with each other and though I wanted my wireless connection to kick in my ethernet connection was still trying to start up as well.

I'm not sure though that you can have an either/or situation. I think you are going to have to select one or the other

I solved the problem by editing my network/interfaces file. I simply hashed out (#) the eth0 entries and then rebooted. This time only my wireless network kicked in and problem solved!

```
sudo gedit /etc/network/interfaces
```

:cool:

---

### Post by OPaul on 2006-02-09
[QUOTE=jcl]Hey OPaul,

I'm sure there is a way to do this, but I've never personally had two separate network interfaces on the same subnet. Post a copy of your 'ifconfig -a' output as well... Just so I understand, you have a hard wired connection and a wireless connection to a wireless router? Is there a reason why you want two interfaces on the same subnet? Is your nameserver different than your default gateway? Can you do an 'nslookup www.yahoo.com'? Can you do a traceroute to your nameserver from network tools?[/QUOTE]

It's a laptop, so sometimes it's sitting on my desk with the ethernet connection and sometimes I take it into the main room and use wireless. I'm assuming the nameservers are the same, it assigned them through DHCP. nslookup doesn't work. Traceroute doesn't work. Both connections have IP addresses though.

```
opaul@dent:~$ ifconfig -a
 eth0      Link encap:Ethernet  HWaddr 00:08:0D:1B:A7:0A
           inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
           inet6 addr: fe80::208:dff:fe1b:a70a/64 Scope:Link
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:7918 errors:0 dropped:0 overruns:0 frame:0
           TX packets:5778 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:7314328 (6.9 MiB)  TX bytes:502666 (490.8 KiB)
 
 lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:52809 errors:0 dropped:0 overruns:0 frame:0
           TX packets:52809 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:4795116 (4.5 MiB)  TX bytes:4795116 (4.5 MiB)
 
 sit0      Link encap:IPv6-in-IPv4
           NOARP  MTU:1480  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
 
 wlan0     Link encap:Ethernet  HWaddr 00:0F:66:3B:C0:02
           inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
           inet6 addr: fe80::20f:66ff:fe3b:c002/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:6707 errors:0 dropped:0 overruns:0 frame:0
           TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:527393 (515.0 KiB)  TX bytes:10079 (9.8 KiB)
           Memory:11000000-110000ff
```

---

### Post by OPaul on 2006-02-09
[QUOTE=AndyCooll]I had a problem similar to this when trying to get my wireless network to work properly. Essentially when booting up both my eth0 and rausb0 connections were conflicting with each other and though I wanted my wireless connection to kick in my ethernet connection was still trying to start up as well.

I'm not sure though that you can have an either/or situation. I think you are going to have to select one or the other

I solved the problem by editing my network/interfaces file. I simply hashed out (#) the eth0 entries and then rebooted. This time only my wireless network kicked in and problem solved!

```
sudo gedit /etc/network/interfaces
```

:cool:[/QUOTE]

Won't that disable the ethernet for good though?

---

### Post by jcl on 2006-02-09
Let me recant my experiences with installing ubuntu... I have a Linksys PCI wireless card that did not work out of the box. My ubuntu box is sitting next to an XP box both with on board ethernet. So in order to connect to the net and download ndiswrapper to get my wireless working, I hard wired the ubuntu box to the xp box (crossover cable of course) and used the xp box as a bridge. My ubuntu box is 192.168.1.103 (I don't use dhcp), so I assigned the on board ethernet to 192.168.1.103 and did my downloading. So when I got the wireless working, I manually disabled eth0 and gave the wireless card (ra0) 192.168.1.103... so I'm thinking you may need to do the same thing and manually disable and enable in the network settings GUI when you want to switch... or just stay wireless even while at your desk? I'm thinking two interfaces on the same subnet just confuses things... perhaps someone can contradict me on this... ?

---

### Post by OPaul on 2006-02-09
[QUOTE=jcl]Let me recant my experiences with installing ubuntu... I have a Linksys PCI wireless card that did not work out of the box. My ubuntu box is sitting next to an XP box both with on board ethernet. So in order to connect to the net and download ndiswrapper to get my wireless working, I hard wired the ubuntu box to the xp box (crossover cable of course) and used the xp box as a bridge. My ubuntu box is 192.168.1.103 (I don't use dhcp), so I assigned the on board ethernet to 192.168.1.103 and did my downloading. So when I got the wireless working, I manually disabled eth0 and gave the wireless card (ra0) 192.168.1.103... so I'm thinking you may need to do the same thing and manually disable and enable in the network settings GUI when you want to switch... or just stay wireless even while at your desk? I'm thinking two interfaces on the same subnet just confuses things... perhaps someone can contradict me on this... ?[/QUOTE]

Yea, I can manually deactivate it fine. But I don't understand why I should have to. Windows has no problem with 2 Internet connections, it just picks one (the fastest I believe). So surely there is a way to get Unbuntu to do the same? Or at the very least automatically deactivate one of them when the other is available.

---

### Post by dockingman on 2006-02-09
Hi guys, I'm having the exact same problem, however when using Kubuntu Breezy... I managed to get an IP address by following the HOWTO at [http://ubuntuforums.org/showthread.php?t=127800](http://ubuntuforums.org/showthread.php?t=127800), however if I unplug the RJ45 from the laptop the connection doesn't stick...

```
englebip@patagonia:~/downloads$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:39:C3:6D:B1
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fec3:6db1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1212192 errors:0 dropped:22 overruns:0 frame:238581
          TX packets:1640406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:291765345 (278.2 MiB)  TX bytes:1833590071 (1.7 GiB)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:B3:23:A4
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:feb3:23a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3440 (3.3 KiB)  TX bytes:2696 (2.6 KiB)
          Interrupt:11 Base address:0x100
```

```
englebip@patagonia:~/downloads$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```

It appears that I don't have a gateway for eth1 (the wireless)... how could I fix this?

Thanks for any help!

---

### Post by Ocxic on 2006-02-10
try this guide it should work for you

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

---

### Post by dcstar on 2006-02-10
[QUOTE=dockingman]
......
```
englebip@patagonia:~/downloads$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
**192.168.0.0**     0.0.0.0         **255.255.255.0**   U         0 0          0 **eth0**
**192.168.0.0**     0.0.0.0         **255.255.255.0**   U         0 0          0 **eth1**
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```

It appears that I don't have a gateway for eth1 (the wireless)... how could I fix this?

Thanks for any help![/QUOTE]
The absolute first thing you should do is make these connections use different IP subnets.

Having two physically different networks using a common IP range is a recipe for problems, the Ubuntu box will believe it can route packets on one of them and expect a reply on the other.

The reason there is no gateway (or routing) to eth1 is that - as far as Ubuntu is concerned - it is the same network as eth0, so why should it change a perfectly good connection for another one on what must be the same network......       :( 

Change one of the networks to something like 192.168.1.x and you may find things work a little differently.

---

### Post by OPaul on 2006-02-10
[QUOTE=Ocxic]try this guide it should work for you

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)[/QUOTE]

Hmm.. links not working for me..

---

### Post by nanotube on 2006-02-10
hey guys
i had the exact same problem - when both eth0 and eth1 are connected, to the same wireless router (and thus the same subnet), there is no network connectivity. 
so essentially i had to resort to your solution - have just one of them plugged/enabled at a time.
it is highly annoying, because windows has no problem with that situation.
you might want to try the network-manager program, that automatically selects and manages connections for you. i just installed it recently, so have not tested it in the presence of both wired and wireless - but according to the docs, it is supposed to handle that situation properly.
check out my howto link on installing network-manager:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles)
(there is a package of network-manager available in the repositories, but it requires you to have bind dns server running on your machine, and that sucks - not to mention sometimes makes dns queries fail. my instructions point you to the location of a modded network-manager without the bind requirement.) 
give it a try, and let know if that solves this problem for you. i will try it in a few days, when i have access to both wired and wireless at the same time, too.

---

### Post by nanotube on 2006-02-10
all right
i have tested the network manager in the case of having both wired and wireless connected to the same router - and the results are great - network manager automatically chooses one of the connections and uses it, without you having to do anything. (it prefers wired over wireless connection, if present). 
so, it seems that network manager is the solution to the original problem.
note, again, that the net manager in the repositories requires bind, and screwed up my dns lookups, so i would suggest you get the modified net manager without bind, as linked to in my previous post.

---

### Post by OPaul on 2006-02-13
Cool, that seems to work. Thanks.

---

### Post by dcstar on 2006-02-13
Now that I fully understand what is being tried to be done here, does anyone think that this would be a better solution (if it works)?:

[http://ubuntuforums.org/showthread.php?t=99668](http://ubuntuforums.org/showthread.php?t=99668)

It should share the traffic between the two interfaces (when both are available), and fall back to a working interface if one went off-line.

It would be interesting to see someone try and get it going with Ethernet and Wireless links.

---

### Post by mips on 2006-02-13
I haven't tried it but in theory it should work. Why don't you give it a bash ? I would if my AP wasn't in for repairs ;)

I would advise thought that that you don't run any of the interfaces at speeds higher than the lowest common denominator. For 54Mb/s wireless & 100Mb/s I would run at 10Mb/s. For 11Mb/s wireless I would try to run both interfaces at round about 5Mb/s. you can always play with these values while using a sniffer to see if you are experiencing layer 2 problems.

Why ? Wireless has a lot of overhead so it performs worse. If you have different speed interfaces you are going to receive out of sync frames which could be very problematic.

---

### Post by nanotube on 2006-02-13
hey
yea, that bonding thing sounds great in theory... except that connecting to the same router, the bottleneck in bandwidth is the uplink to the isp, anyway, so it wouldnt result in any speed gains.
(ie, my wifi to router: 54mbps, wired to router: 100mbps, router to cable modem: 100mbps, cable modem isp uplink: **6 mbps**). so in "most" cases where you have two nics or more connected to a common router, you are hitting the bottleneck at the uplink, so the bonding idea is of little use.

---

### Post by mips on 2006-02-13
[QUOTE=nanotube]hey
yea, that bonding thing sounds great in theory... except that connecting to the same router, the bottleneck in bandwidth is the uplink to the isp, anyway, so it wouldnt result in any speed gains.
(ie, my wifi to router: 54mbps, wired to router: 100mbps, router to cable modem: 100mbps, cable modem isp uplink: **6 mbps**). so in "most" cases where you have two nics or more connected to a common router, you are hitting the bottleneck at the uplink, so the bonding idea is of little use.[/QUOTE]

Correct, unless you use it somewhere like work with high-speed internet or your purpose is some sort of resilience.

---

### Post by dcstar on 2006-02-13
[QUOTE=nanotube]hey
yea, that bonding thing sounds great in theory... except that connecting to the same router, the bottleneck in bandwidth is the uplink to the isp, anyway, so it wouldnt result in any speed gains.
(ie, my wifi to router: 54mbps, wired to router: 100mbps, router to cable modem: 100mbps, cable modem isp uplink: **6 mbps**). so in "most" cases where you have two nics or more connected to a common router, you are hitting the bottleneck at the uplink, so the bonding idea is of little use.[/QUOTE]
Agreed, but for the purposes of people wanting to use **both** their wired and wireless connections to the same router - automagically using them without user intervention - it might be worth trying.

BTW - I don't have an AP so I can't find out for myself if it is viable!

---

### Post by nanotube on 2006-02-14
mips: i agree that there are situations where it would be useful. i was just saying that for most situations on the "home user" front, it will not provide any benefit.

dcstar: network-manager already does allow you to automagically switch between wired/wireless without user intervention. it automatically chooses the fastest link and uses it. but like i said, doesnt mean the bonding thing is useless, just probably not very useful for most home users. still, could be a very interesting alternative way of doing this. :)

---

### Post by dcstar on 2006-02-14
[QUOTE=nanotube]......
dcstar: network-manager already does allow you to automagically switch between wired/wireless without user intervention. it automatically chooses the fastest link and uses it. but like i said, doesnt mean the bonding thing is useless, just probably not very useful for most home users. still, could be a very interesting alternative way of doing this. :)[/QUOTE]
Ok, I still thought it was a manual process - thanks.

---

### Post by nanotube on 2006-02-14
no prob.
net-man really is cool. it's what connection management in ubuntu should be, but isnt. i hear it will be the default way of managing connections in dapper.
if you are using a laptop yourself, i highly recommend it. 
(doesnt really do anything for a desktop with a persistent wired connection, though :) ).

---

