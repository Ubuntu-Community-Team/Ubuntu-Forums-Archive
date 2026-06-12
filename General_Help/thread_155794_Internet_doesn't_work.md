---
title: "Internet doesn't work"
date: 2006-04-05
forum: General Help
---

### Post by _linux_ on 2006-04-05
I set up ndiswrapper for my DWL-G510 D-Link card. It worked great the first time. But the next time, I was connected but couldn't load any web pages. I got a "Connection refused by www.google.com" message from Firefox. Does anyone know what's wrong?

---

### Post by dcstar on 2006-04-05
[QUOTE=_linux_]I set up ndiswrapper for my DWL-G510 D-Link card. It worked great the first time. But the next time, I was connected but couldn't load any web pages. I got a "Connection refused by www.google.com" message from Firefox. Does anyone know what's wrong?[/QUOTE]
Open a terminal and run:
```
ifconfig
route -n
traceroute www.google.com
```
and post the results here.

---

### Post by _linux_ on 2006-04-06
Okay here is what I got:

```
ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:74:B7:30
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe74:b730/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:823 errors:31376 dropped:0 overruns:0 frame:31376
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:272060 (265.6 KiB)  TX bytes:1062 (1.0 KiB)
          Interrupt:11 Memory:cea20000-cea30000

eth0      Link encap:Ethernet  HWaddr 00:50:BF:A2:CF:B5
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fea2:cfb5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:412489 (402.8 KiB)  TX bytes:412489 (402.8 KiB)
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

traceroute didn't work, but I did get this:
```
Network device:	ath0
Hardware address:	00:13:46:74:b7:30
IP address:	192.168.0.100
Netmask:	255.255.255.0
Broadcast:	192.168.0.255
Multicast:	Enabled
MTU:	1500
Link speed:	36 Mbps
State:	Active
Transmitted packets:	7
Transmission errors:	0
Received packets:	1176
Reception errors:	49633
Collisions:	0

```

---

### Post by drberg1000 on 2006-04-07
If your setup is like that of my laptop, then eth0 is a wired interface.  If you aren't using that right now, try taking it down with the command:

```
sudo ifdown eth0
``` 
This way we know that eth0 isn't causing any problems.

A few more commands to try and find the problem:

```

ifconfig ath0
iwconfig ath0
route -n
ping 192.168.0.1
ping 72.14.207.99

``` 
The second ping is to one of google's servers.  Using the IP instead of the name eliminates DNS.

To bring eth0 back up use:

```
sudo ifup eth0
``` 
If you want to revert to the way the network is setup on boot run:
```
sudo /etc/init.d/networking restart
``` 
--Dave

---

### Post by _linux_ on 2006-04-07
Okay, this is what I got:

```
ifconfig ath0:

ath0      Link encap:Ethernet  HWaddr 00:13:46:74:B7:30
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1159 errors:1326 dropped:0 overruns:0 frame:1326
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:377242 (368.4 KiB)  TX bytes:10335 (10.0 KiB)
          Interrupt:11 Memory:cea20000-cea30000
--------------------------------------------------------------------------------------
iwconfig ath0:

ath0      IEEE 802.11g  ESSID:"xxxx"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:46:B7:83:A6
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/94  Signal level=-75 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--------------------------------------------------------------------------------------
route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
---------------------------------------------------------------------------------------
ping 192.168.0.1:

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=6.47 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=2.85 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=2.63 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=9.35 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=2.78 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4040ms
rtt min/avg/max/mdev = 2.636/4.821/9.352/2.686 ms
----------------------------------------------------------------------------------------
ping 72.14.207.99:

PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=244 time=84.7 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=244 time=95.0 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=244 time=90.1 ms
64 bytes from 72.14.207.99: icmp_seq=4 ttl=244 time=84.4 ms
64 bytes from 72.14.207.99: icmp_seq=5 ttl=244 time=86.4 ms

--- 72.14.207.99 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 84.485/88.164/95.001/3.984 ms
```

Since it pinged Google's IP address correctly, does that mean there's a DNS problem? If there is, how do I fix it?

---

### Post by drberg1000 on 2006-04-07
[QUOTE=_linux_]Okay, this is what I got:

ping 72.14.207.99:

PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=244 time=84.7 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=244 time=95.0 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=244 time=90.1 ms
64 bytes from 72.14.207.99: icmp_seq=4 ttl=244 time=84.4 ms
64 bytes from 72.14.207.99: icmp_seq=5 ttl=244 time=86.4 ms

--- 72.14.207.99 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 84.485/88.164/95.001/3.984 ms[/CODE]

Since it pinged Google's IP address correctly, does that mean there's a DNS problem? If there is, how do I fix it?[/QUOTE]

Yes, if you can ping 72.14.207.99 but not google.com, then you have a DNS problem.  If you haven't already tried, ping google.com again to make sure that the problem wasn't fixed by taking eth0 down. 

What kind of gateway do you use?  My Actiontec from QWest has dns problems and I have to bypass it.  Also, I'm assuming that you are using DHCP.  To fix the problem, you need to find out what DNS servers you should be using.  Some times you can get these from your modem's web interface, you could also get them by calling your ISP or looking at the paperwork you got from them when you signed up.  If you have access to a windows machine you could also get the numbers from there.  

You may already know this but just to make sure, you are looking for an IP address or two with the name DNS or Domain Name Server or something similar.

Once you have these numbers you need to edit /etc/resolv.conf and change the "nameserver  XXX.XXX.XXX.XXX" lines accordingly.

Let me know if that works and I'll tell you how to set it up so it will work on reboot.

--Dave

---

### Post by _linux_ on 2006-04-07
It's working!!!! :D  Turns out it wasn't a DNS problem. It was fixed because I disabled IPv6 or because I deactivated eth0. Thanks for everyone's help! :KS

---

### Post by _linux_ on 2006-04-08
Okay, I checked and the problem was that eth0 was activated. ](*,)  Is there any way to make sure it's never activated on boot?

---

### Post by _linux_ on 2006-04-10
I think I have to edit /etc/init.d/networking for eth0 not to activate on boot. But  how?

---

### Post by poor_kenny on 2006-06-17
[QUOTE=drberg1000]
What kind of gateway do you use?  My Actiontec from QWest has dns problems and I have to bypass it.  Also, I'm assuming that you are using DHCP.  To fix the problem, you need to find out what DNS servers you should be using.  Some times you can get these from your modem's web interface, you could also get them by calling your ISP or looking at the paperwork you got from them when you signed up.  If you have access to a windows machine you could also get the numbers from there.  

You may already know this but just to make sure, you are looking for an IP address or two with the name DNS or Domain Name Server or something similar.

Once you have these numbers you need to edit /etc/resolv.conf and change the "nameserver  XXX.XXX.XXX.XXX" lines accordingly.

Let me know if that works and I'll tell you how to set it up so it will work on reboot.

--Dave[/QUOTE]

Dave; I'd like to know how to set that up to work on reboot. I have a ActionTec from Qwest as well, and have to change *one* of the nameservers to get it to work everytime.

Incidently, the resolv.conf file seems to be a user session generated file. Sometimes I go to edit it and nothing is there. I have to change one of the nameservers through the Administration>Networking (Network settings)>DNS tab.

What did you do?

Thanks.
~Scott

---

### Post by drberg1000 on 2006-06-17
As root, edit the file /etc/dhcp3/dhclient.conf.

Ignoring comments, my file looks like this:

supersede domain-name-servers 205.171.2.65;
prepend domain-name-servers 205.171.3.65;

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;


The "supersede" and "prepend" lines are most likely all you need to add.  Though the name servers you want to use are most likely different.  If you left your actiontec in its default state you should be able to point your browser to: 192.168.0.1 and follow the status link to get your DNS servers.  
There may be a way to do this in the System/Admin/Networking dialog but I haven't played with it.

If the request line is there but different or not there I wouldn't worry about it assuming everything else works fine.  The defaults are probably adequate.

Let me know if you need anything else.

--Dave

---

