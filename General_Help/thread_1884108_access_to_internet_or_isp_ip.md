---
title: "access to internet or isp ip"
date: 2011-11-20
forum: General Help
---

### Post by stanjest on 2011-11-20
Hello;
I can access by router, I can ping my router, my router is connected to the internet, but I cannot ping my ISP dns ip address on the ubuntu machine. Any suggestion is welcome.
Thanks in advance

---

### Post by hal8000 on 2011-11-20
Most likely a problem with /etc/resolv.conf

Post output of:
sudo cat /etc/resolv.conf

Example
[anc@slave ~]$ cat /etc/resolv.conf
nameserver 192.168.254.254


The nameserver can contain the IP address of your router, your ISP's DNS servers or if allowed by your ISP OpenDNS or Google DNS 8.8.8.8

---

### Post by dabl on 2011-11-20
Wired or wireless?
Has the router been working with other computer(s)?
Post your /etc/networking/interfaces file
Post the output of 

```
sudo ifconfig
```

That should get us started.

---

### Post by stanjest on 2011-11-20
I had check the /etc/resolv.conf, it contains the ip address of the isp, plus 192.168.1.1, my router. 
ifconfig provides normal output.
I can access the webpages of my router, no problems.
Just cannot get to the isp. Cannot ping it either.

---

### Post by fdrake on 2011-11-20
> **stanjest said:**
> I had check the /etc/resolv.conf, it contains the ip address of the isp, plus 192.168.1.1, my router. 
ifconfig provides normal output.
I can access the webpages of my router, no problems.
Just cannot get to the isp. Cannot ping it either.

check the confi of your router or modem? do you use authentication? is it set up to DHCP?

---

### Post by stanjest on 2011-11-20
> **fdrake said:**
> check the confi of your router or modem? do you use authentication? is it set up to DHCP?
I have several windows machine connected to the same router, all working ok. The connection to the linux machine was operational previously. it stop working after I attempted to add another NIC card into the system, the new NIC card had since been removed.
All references to the new NIC card was removed from \etc\interfaces, etc. The router dhcp clients list show the linux PC connection.

---

### Post by dabl on 2011-11-20
Do you have a DNS search line in /etc/network/interfaces?

Can you ping anything outside your router -- google.com, for example?

---

### Post by stanjest on 2011-11-20
no I deleted it. and no I cannot get pass the dns or ISP. cannot ping either ip address. could it be something with ipv6, the ip connections goes dead once it a while, I had to edit the connection and change the ipv6 to ignore, it re-establish itself.

---

### Post by stanjest on 2011-11-20
here are the listing requested earlier
eth0      Link encap:Ethernet  HWaddr 00:1e:90:c9:62:5f  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fec9:625f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2222758 (2.2 MB)  TX bytes:606084 (606.0 KB)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

content of /etc/network
drwxr-xr-x   6 root root  4096 2011-11-19 20:20 .
drwxr-xr-x 130 root root 12288 2011-11-20 17:47 ..
drwxr-xr-x   2 root root  4096 2011-09-24 20:20 if-down.d
drwxr-xr-x   2 root root  4096 2011-09-24 20:14 if-post-down.d
drwxr-xr-x   2 root root  4096 2011-02-11 08:22 if-pre-up.d
drwxr-xr-x   2 root root  4096 2011-09-24 20:20 if-up.d

content of dhclient
steven@steven-desktop:/etc/network$ sudo dhclient eth0
[sudo] password for steven: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1e:90:c9:62:5f
Sending on   LPF/eth0/00:1e:90:c9:62:5f
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.110 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.110 from 192.168.1.1
bound to 192.168.1.110 -- renewal in 33334 seconds.
steven@steven-desktop:/etc/network$

---

### Post by newbie-user on 2011-11-20
check the route from the ubuntu machine.  type "route" at the command prompt to see if your ubuntu machine is going in the right direction.  if not, you might manually specify the default gateway settings.

---

### Post by stanjest on 2011-11-20
here is the posting for the route
steven@steven-desktop:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
is it the right direction?

---

### Post by fdrake on 2011-11-20
> **stanjest said:**
> here is the posting for the route
steven@steven-desktop:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
is it the right direction?

everything looks fine to me from your files.
can you give as the result for :
```

traceroute google.com

```
i just want to see where you get stuck!also post
less /etc/network/interfaces

---

### Post by stanjest on 2011-11-20
route posting

steven@steven-desktop:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

hope these helps

---

### Post by stanjest on 2011-11-20
can't traceroute. a. I do not have that pkg installed and b. I cannot get pass my isp. cannot even reach my isp.

---

### Post by stanjest on 2011-11-20
I actually solved the problem.
When I did the route command, I executed route -FC which gives more  info on the route tables. I notice I had got a error ip address 1921.68.1.255 stuck in the table. More reading, I came across the ip route command. I manage to flush the error ip address from the route table, and everything works.
Thanks to all that contributed. I hope this helps other people too.
Please mark this as solved. I have not idea how to do it. Thanks

---

