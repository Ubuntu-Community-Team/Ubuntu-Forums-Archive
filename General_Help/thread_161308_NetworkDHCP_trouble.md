---
title: "Network/DHCP trouble"
date: 2006-04-16
forum: General Help
---

### Post by Caesar_Harrington on 2006-04-16
Hi, I have a number of network problems with ubuntu 5.10.
It starts during the installation process, when the program times out during the dhcp section. It won't get through to the router to setup a proper ip and gateway. I've tried two different routers, both of which funtion well when I'm running XP.

Ubuntu recognizes my network card, so the problem is not that the driver's missing. I've tried both static and DHCP settings in ubuntu and neither worked. I can't ping any outside ip address, not even the router (a wireless topcom skyr@cer 254g, though wired to my comp). 

I've searched everywhere for a solution to this problem but nothing seems to help. 
I'm sorry if I haven't been specific enough, I'm a total newbie when it comes to linux.

Cheers,
C

---

### Post by mscman on 2006-04-16
can you give the results of running:
```
ifconfig -a
```

---

### Post by Caesar_Harrington on 2006-04-16
Ok here goes
```

eth0 Link encap:Ethernet HWaddr 00:30:F1:34:7B:18
       inet addr: 192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
       Interrupt: 11 Base address:0x9000

lo     Link encap: Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       UP LOOPBACK RUNNING  MTU:16436 Metric:1
       RX Packets: 5 errors:0 dropped:0 overruns:0 frame:0
       TX Packets: 5 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 tqueuelen:0
       RX bytes:272 (272.0 b) TX bytes:272 (272.0 b)

```

That's it. Thanks for helping.

---

### Post by pitkali on 2006-04-16
Check, if this helps for a start:
```
sudo route add default gw *your.router.IP.address*
```

---

### Post by Caesar_Harrington on 2006-04-16
[QUOTE=pitkali]Check, if this helps for a start:
```
sudo route add default gw *your.router.IP.address*
```[/QUOTE]

Nope, didn't help, I already set the gateway though.

Cheers

---

### Post by harisund on 2006-04-16
[QUOTE=Caesar_Harrington]Ok here goes
```

eth0 Link encap:Ethernet HWaddr 00:30:F1:34:7B:18
       inet addr: 192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
       Interrupt: 11 Base address:0x9000

lo     Link encap: Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       UP LOOPBACK RUNNING  MTU:16436 Metric:1
       RX Packets: 5 errors:0 dropped:0 overruns:0 frame:0
       TX Packets: 5 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 tqueuelen:0
       RX bytes:272 (272.0 b) TX bytes:272 (272.0 b)

```.[/QUOTE]

Your ifconfig output makes me think it already has internet. Just try something along the lines of```
ping -c 5 www.google.com
``` and see if it is able to access the internet. I am thinking it will be able to.

---

### Post by Caesar_Harrington on 2006-04-16
[QUOTE=harisund]Your ifconfig output makes me think it already has internet. Just try something along the lines of```
ping -c 5 www.google.com
``` and see if it is able to access the internet. I am thinking it will be able to.[/QUOTE]

No, it says:

```

ping -c 5 www.google.com
ping: unknown host www.google.com

```

---

### Post by pitkali on 2006-04-16
>  and see if it is able to access the internet. I am thinking it will be able to.
I don't think so. Notice that eth0 has a UP flag, but not RUNNING. AFAIR both should be present (and are on my laptop). It's actually strange, lack of one of them.

Actually, what kind of network card is that? How did you configure it?

And try simply ```
sudo dhclient eth0
```

---

### Post by rvergara on 2006-04-16
are you able to ping your gateway?

ping 192.168.1.XXX

where XXX is your gateway ip in your LAN.

Do you have a single router in your LAN?

Ramiro

---

### Post by bluetoad on 2006-04-16
Let's just check the route's and gateways once more with 

netstat -nr

What are the contents of your /etc/resolv.conf file?  That file can be generated through the GUI with System/Networking on the DNS tab for the appropriate interface.

---

### Post by Caesar_Harrington on 2006-04-17
[QUOTE=pitkali]I don't think so. Notice that eth0 has a UP flag, but not RUNNING. AFAIR both should be present (and are on my laptop). It's actually strange, lack of one of them.

Actually, what kind of network card is that? How did you configure it?

And try simply ```
sudo dhclient eth0
```[/QUOTE]

It's a 10/100 PCI one (acceton I think). It was detected correctly by ubuntu and i've configured it in gnome. Dhclient won't work, says it doesn't get a response.

---

### Post by Caesar_Harrington on 2006-04-17
[QUOTE=rvergara]are you able to ping your gateway?

ping 192.168.1.XXX

where XXX is your gateway ip in your LAN.

Do you have a single router in your LAN?

Ramiro[/QUOTE]

No, I can't ping the gateway. I connect to the internet via an ADSL modem/router. That only has one port and that one is wired to a topcom skyr@cer 254G router. That router in turn is wired to the comp I'm having the problems with.

---

### Post by Caesar_Harrington on 2006-04-17
[QUOTE=bluetoad]Let's just check the route's and gateways once more with 

netstat -nr

What are the contents of your /etc/resolv.conf file?  That file can be generated through the GUI with System/Networking on the DNS tab for the appropriate interface.[/QUOTE]

When i type 
```
netstat -r
```

it says
```

Destination       Gateway          Genmask                   Flags   MSS Window      irtt  Iface
192.168.1.0      0.0.0.0            255.255.255.255.0      U            0 0                 0  eth0
0.0.0.0            192.168.1.1      0.0.0.0                     UG           0 0                0  eth0

```

It's strange that the first destination is 192.168.1.0 when my router's ip 192.168.1.1 and that's what i set it to in system/Networking. 

My resolv.conf looks like this:
```

nameserver 192.168.1.1



```

---

### Post by rvergara on 2006-04-17
your netstat -nr  result is fine, the first destination is just your LAN area (the result of the boolean operation with your mask).

that result says that your gateway is 192.168.1.1.. It does not matter how physically you connect to the internet, you MUST have connectivity with your gateway. please ping 192.168.1.1 and report the result.

Thanks

Ramiro

---

### Post by Caesar_Harrington on 2006-04-17
[QUOTE=rvergara]your netstat -nr  result is fine, the first destination is just your LAN area (the result of the boolean operation with your mask).

that result says that your gateway is 192.168.1.1.. It does not matter how physically you connect to the internet, you MUST have connectivity with your gateway. please ping 192.168.1.1 and report the result.

Thanks

Ramiro[/QUOTE]

Ok

```

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable
From 192.168.1.1 icmp_seq=5 Destination Host Unreachable
From 192.168.1.1 icmp_seq=6 Destination Host Unreachable
From 192.168.1.1 icmp_seq=7 Destination Host Unreachable
From 192.168.1.1 icmp_seq=8 Destination Host Unreachable
From 192.168.1.1 icmp_seq=10 Destination Host Unreachable
From 192.168.1.1 icmp_seq=11 Destination Host Unreachable
From 192.168.1.1 icmp_seq=12 Destination Host Unreachable
From 192.168.1.1 icmp_seq=14 Destination Host Unreachable
From 192.168.1.1 icmp_seq=15 Destination Host Unreachable
From 192.168.1.1 icmp_seq=16 Destination Host Unreachable
From 192.168.1.1 icmp_seq=18 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
33 packets transmitted, 0 received, +24 errors, 100% packet loss, time 32002 ms, pipe 3


```

I omitted some of the Destination Host Unreachable rows...

Cheers 
C

---

### Post by Caesar_Harrington on 2006-04-17
I just re-installed ubuntu, and re-configured the network card in gnome.

now when i type
```

ifconfig -a

```


it says

```

eth0   Link encap: Ethernet   HWaddr 00:30:F1:34:7B:18
         inet addr.192.168.0.101 Bcast.192.168.1.255 Mask:255.255.255.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:15 overruns:0 frame:0
         TX packets:0 errors:0 dropped:15 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
         Interrupt:11 Base  address:0x900

lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:5353 errors:0 dropped:0 overruns:0 frame:0
        TX packets:5353 errors:0 dropped:0 overruns:0 carrier:0
        collision:0 tqueuelen:0
        RX bytes:484948 (473.5 KiB)   TX bytes:484948 (473.5 KiB)

```

Oh, and I also deactived ipv6 by

```

sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

sudo depmod -a

```

Cheers 
C

---

### Post by rvergara on 2006-04-17
there is a problem in your network configuration. Your PC ip address and your gateway address are NOT in the same network.

192.168.0.101 is not in the same network as 192.168.1.1.

Please change your PC ip address to 192.168.1.X and it should work fine.

Regards

Ramiro

---

### Post by Caesar_Harrington on 2006-04-17
[QUOTE=rvergara]there is a problem in your network configuration. Your PC ip address and your gateway address are NOT in the same network.

192.168.0.101 is not in the same network as 192.168.1.1.

Please change your PC ip address to 192.168.1.X and it should work fine.

Regards

Ramiro[/QUOTE]

Actually, that was a type-o. It said 192.168.1.101 already *stupid* :)

---

### Post by Caesar_Harrington on 2006-04-17
Something interesting (or frustrating) is that when I check the router from my laptop with XP it says that an unknown host is connected to 192.168.1.101

Still, I can't ping the router/gw...

This is just really frustrating.

Thanks for the replies everyone

---

### Post by Angry penguin on 2006-04-17
I am having the same problem, what does it give you from running iwconfig? Mine looks fine but I don't appear to have an access point it says:

Access Point: 00:00:00:00:00:00

I tried to define the ap by typing 

iwconfig wlan0 ap (Access Point)

but that didnt work, it just returns the same zeros in that field.

---

### Post by pitkali on 2006-04-17
What does ```
iwlist eth0 scan
``` say?

---

### Post by Caesar_Harrington on 2006-04-17
[QUOTE=pitkali]What does ```
iwlist eth0 scan
``` say?[/QUOTE]

I am not trying to connect using a wlan card, but a regular one. I am using a topcom skyr@cer but I have my comp wired to one of the router's four ports. Sorry for confusion, I thought i mentioned it in my first post.

---

### Post by pitkali on 2006-04-17
I asked the other person. You did indeed mention having wired connection ;)

---

### Post by rabidphage on 2006-04-17
almost same wierd problem here

darx@darx:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:ce:3c:ce:3c
Sending on   LPF/eth0/00:13:ce:3c:ce:3c
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 172.25.24.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 172.25.24.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.25.24.1
SIOCADDRT: Network is unreachable
bound to 172.25.26.240 -- renewal in 1783 seconds.

Everything seems fine however the network is unreachable

---

### Post by Angry penguin on 2006-04-17
it tells me:

Interface doesn't support scanning : Resource temporarily unavailable

---

### Post by Angry penguin on 2006-04-17
here is some info:

this gets me connected to the network:
root@slax:~# ifconfig wlan0 123.123.123.123 netmask 255.255.255.0

root@slax:~# route add default gw 192.168.0.1
SIOCADDRT: Network is unreachable
root@slax:~# dhcpcd -t 20 wlan0
root@slax:~#                     

at this point it disconnects from the network

If I reenter the ifconfig command above it connects to the network but I cant ping the router or anything outside.

root@slax:~# ifconfig wlan0 192.168.0.140 netmask 255.255.255.0
root@slax:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.140 icmp_seq=1 Destination Host Unreachable
From 192.168.0.140 icmp_seq=2 Destination Host Unreachable
From 192.168.0.140 icmp_seq=3 Destination Host Unreachable

---

### Post by pitkali on 2006-04-18
It can't work - you didn't associate card with access point using iwconfig command, so the driver doesn't know where to send packets over the air. BTW: you were scanning eth0 or wlan0? Because despite what I wrote you should've scanned wlan0 ;)

---

### Post by Angry penguin on 2006-04-18
i did specify the access point with:

iwconfig wlan0 ap ...........

but it didnt fix it, the ap remained 00:00:00:00:00. The command returned no errors or anything.

---

### Post by pitkali on 2006-04-18
Are you sure your wlan card is supported and its support configured?

---

### Post by Angry penguin on 2006-04-19
Yep, its an acx 111 chipset supported by the Texas Instruments acx 111 driver.

---

### Post by Angry penguin on 2006-04-24
anybody got any ideas?

---

### Post by lazy44 on 2006-04-24
i dont have a host it say unknow   what do i do?

---

### Post by rabidphage on 2006-04-25
This will definitely help i suppose
Log into the windows.
Go to command prompt or whatever it is. type ipconfig /release
press enter immediately
reboot into ubuntu. hopefully if you haven't messed up anything while troubleshooting  it'll probably connect.
The reason is that windows doesn't release the dhcp lease when shutting down. I've heard that neither does ubuntu. however windows always manages to connect.
BTW do i know you??

---

### Post by Angry penguin on 2006-04-25
I should have mentioned I am not dual booting, I have another machine running windows, which I used to find the default gateway and other critical information so that I could specify it inside ubuntu.

---

### Post by rabidphage on 2006-04-26
if its dhcp, the network manager will probably do all the configuration for you. you don't have to enter the netmask and stuff.
try removing all the information that you have entered, bring down all the interfaces other than the once you are connectiong with. 
use ifconfig ethx down where x is the specific interface. then try restarting the network as in the previous posts.
just to be sure check the router configuration via its htttp interface

---

