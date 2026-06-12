---
title: "keeping the same internal IP address"
date: 2012-09-30
forum: General Help
---

### Post by micahpage on 2012-09-30
I was running a server and noticed that every time I reboot, I have to reset all my port forwards in the router to adjust to my new internal IP address each time I reboot my PC, making it a hassle.

Is there a way to keep or maintain the same internal IP address for a specific computer on a network regardless of reboots, etc.?

---

### Post by Vaphell on 2012-09-30
if your router has the option to assign fixed ip to a given mac address, use that - it should be somewhere in dhcp options. If that's not the case, you always have an option to disable dhcp autoconfiguration and set ip by hand.

---

### Post by cjhabs on 2012-09-30
I am on 10.04 so YMMV, but right clicking on the network icon in the top bar allows you to edit connections. There you can edit the IPv4 settings to set a manual IP address and DNS

---

### Post by kjohri on 2012-09-30
Instead of DHCP, you can use static IP address set manually. Just click the networking applet icon, edit connections and in the IPV4 settings, change Method to Manual. Enter the address, netmask and gateway.

---

### Post by micahpage on 2012-09-30
I just recently got a new router and not sure of how to navigate through it to find the dhcp settings. IT is a Netgear using Geany wnr2000v3

I don't see an option for DHCP

I do see an option for internal ip addres to either get dynamically from ISP or use static IP address. But none of the options allow a mac address

EDIT:
what is the ip address, ip subnet mask, and gateway ip address differences in:

```
metulburr@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr aa:00:04:00:0a:04  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a800:4ff:fe00:a04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16878537 (16.8 MB)  TX bytes:3114815 (3.1 MB)
          Interrupt:53 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88976 (88.9 KB)  TX bytes:88976 (88.9 KB)

metulburr@ubuntu:~$ 

```

the default ip's on the router settings show the public ip address, a subnet mask ip, and a number i have never seen before in the gateway

---

### Post by Vaphell on 2012-09-30
[http://screenshots.portforward.com/Netgear/WNR2000v3/Address_Reservation.htm](http://screenshots.portforward.com/Netgear/WNR2000v3/Address_Reservation.htm)

i'd check this options page, if i were to guess, i'd say it can be used to make the router assign fixed ip to devices that match the criteria.

---

### Post by micahpage on 2012-10-01
that is what my old netgear software (v2) looked like, but this new software for it, looks totally different (v3).  I looked through each section possible and couldn't find a page that looked like that or somewhat looked like that.

---

### Post by oldfred on 2012-10-01
Most newer routers let you set a fixed it there. But be sure if configuring from PC that you do not select a address that is inside the default DHCP range.

Also do not mix gui methods and command line file edits as they conflict.

Most of us use the gui to set a fixed IP. But if you have a server without gui then you have to edit files or manually set each reboot. 

 Changing IP Addresses and Routes at command line:
[http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)

Last option is to configure the more old-school way. You edit /etc/network/interfaces to look a bit like this (making sure you avoid addresses that the DHCP server might lease to other PCs but still using addresses in the same network number):
Quote:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
and edit /etc/resolv.conf to have an entry for your name server like this:
Quote:
nameserver 192.168.1.1 

route -n
Example: 192.168.1.1 UG
U indicates if its up and G tells you its your gateway!

fred@fred-Precise:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX 
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe20:e2a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128108111 (128.1 MB)  TX bytes:8822777 (8.8 MB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:705838 (705.8 KB)  TX bytes:705838 (705.8 KB)

fred@fred-Precise:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

---

### Post by lisati on 2012-10-01
The two main methods I'm aware of for setting a fixed address have been mentioned. On my newest modem/router (not a NetGear), the relevant option is found under "Home Network", and requires clicking on the entry relevant for the machine you are interested in, then clicking on "Configure."

---

### Post by steeldriver on 2012-10-01
on my Netgear WNDR3800 the procedure via the routerlogin.net web interface is this:

1. select the ADVANCED tab

2. select Setup --> LAN Setup

3. static IPs can be set via the Address Reservation section at the bottom

This is the same page you would need to go to to make sure any client-side static address you set is outside the DHCP range

---

