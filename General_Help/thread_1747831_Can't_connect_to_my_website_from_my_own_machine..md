---
title: "Can't connect to my website from my own machine."
date: 2011-05-03
forum: General Help
---

### Post by Krauser Joestar on 2011-05-03
Hey there everyone

So, i have created some php pages on ubuntu(which is installed on a virtual machine) and i can access them just fine from there.

However, from my host(W7), i can't connect to the page or even ping it, as it says all the time that the connection expired.

What should i do?

---

### Post by Krauser Joestar on 2011-05-03
Anyone?

---

### Post by Krauser Joestar on 2011-05-03
Anyone?
So i have just tried setting the virtualbox for bridged adapter and still nothing. I don't know what to do

here's my ifconfig and ipconfig

ipconfig

Wireless LAN adapter Wireless Network Connection:

 Media State . . . . . . . . . . . : Media disconnected
 Connection-specific DNS Suffix . :

Ethernet adapter VirtualBox Host-Only Network:

 Connection-specific DNS Suffix . :
 Link-local IPv6 Address . . . . . : fe80::864:2178:5954:575d%20
 IPv4 Address. . . . . . . . . . . : 192.168.56.1
 Subnet Mask . . . . . . . . . . . : 255.255.255.0
 Default Gateway . . . . . . . . . :

ping 192.168.0.2

Pinging 192.168.0.2 with 32 bytes of data:
Reply from 192.168.234.250: TTL expired in transit.
Reply from 192.168.234.250: TTL expired in transit.
Reply from 192.168.234.250: TTL expired in transit.
Reply from 192.168.234.250: TTL expired in transit.


ifconfig


eth0 Link encap:Ethernet HWaddr 08:00:27:d4:3c:f8 
 inet6 addr: fe80::a00:27ff:fed4:3cf8/64 Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000 
 RX bytes:0 (0.0 B) TX bytes:5612 (5.6 KB)


eth0:1 Link encap:Ethernet HWaddr 08:00:27:d4:3c:f8 
 inet addr:192.168.0.2 Bcast:192.168.0.255 Mask:255.255.255.0
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1


lo Link encap:Local Loopback 
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:16436 Metric:1
 RX packets:8 errors:0 dropped:0 overruns:0 frame:0
 TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0i txqueuelen:0 
 RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)

---

### Post by Peter09 on 2011-05-03
You do seem to have some problems with your network set up.
 
Is your host connected to a router? 
 
My guess is that your virtual machine is set up as an internal network. When you try to get to it your host is going out to your router which knows nothing about your Virtual Machine.
 
Perhaps set your Virtual Machine up as a bridged network so that it can get its IP address from your router.

---

### Post by Krauser Joestar on 2011-05-03
> **Peter09 said:**
> 
 
Perhaps set your Virtual Machine up as a bridged network so that it can get its IP address from your router.

I've tried that already on my virtualbox, it didn't work out unfortunately. The ip stays static and as such, the same ip. MayBE i have to restart the virtual machine for this to take effect.

however, when i do a ipconfig on my host, it always appears ethernet adapter virtualbox host-only network and the ipv4 as 192.168.56.1

The ip of the virtualbox is 10.0.2.15 and i want my host to access the web page done on my virtualbox, which has this ip 192.168.0.2

---

### Post by Peter09 on 2011-05-03
You need to set your virtual machine as a bridged system with an ip address using DHCP from your router. That is the simplest way. Your system will then see your virtual machine as being on your local network.

---

### Post by a2j on 2011-05-03
pretty sure they both need to be on the same network (i.e. 192.168.0.) unless you have router in between to route the packets between two totally different networks.

---

### Post by morrty11 on 2011-05-03
Is there a router in play here? From your ipconfig printout, it doesn't look like it.

You can't ping other subnets (192.168.0.xxx) if there is no router.

---

### Post by Krauser Joestar on 2011-05-04
> **morrty11 said:**
> Is there a router in play here? From your ipconfig printout, it doesn't look like it.

You can't ping other subnets (192.168.0.xxx) if there is no router.


Yeah i can't ping those subnets. I'm working on an enterprise, so i wanted to let everyone and myself access to my pages hosted on my guest. 

I think i should post everything that i've done here, besides the ipconfig/ifconfig outputs(btw i have already set up the network adapter for bridged adapter but still nothing.


**interfaces:**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[B]iface eth0:1 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1[/B]



VirtualHost 192.168.0.2>



**resolv.conf**
nameserver 192.168.0.2 -> **my domain**
nameserver 10.64.45.15
nameserver 10.64.45.14
nameserver 10.64.45.12
nameserver 10.64.192.100
nameserver 10.64.200.100
nameserver 10.64.200.101
domain xxx.xxx.xxx -> **the local domain**
search xxx.xxx.xxx 



**hosts**
27.0.0.1       localhost
127.0.1.1       xx.xxx
192.168.0.2     [B]my domain




about the organization

[/B]Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : xxx.xxx.xxx
   Link-local IPv6 Address . . . . . : fe80::e8e4:b28f:3d87:fab5%12
   IPv4 Address. . . . . . . . . . . : 10.64.46.20
   Subnet Mask . . . . . . . . . . . : 255.255.252.0
   Default Gateway . . . . . . . . . : 10.64.47.254Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::864:2178:5954:575d%20
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Tunnel adapter isatap.{4A2BE83F-9F7E-499D-9972-7A0457F38502}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

---

### Post by Krauser Joestar on 2011-05-04
bump

Sorry for being a pain but i really need to get this working.

---

### Post by satanselbow on 2011-05-04
May be not quite the solution you are looking for but it may be simpler (and a hell of a lot quicker to implement);

Why not use a shared folder as your webroot and run a localserver on your W7 host pointed to the same location? Installing WAMP on W7 doesn't take long to set up (not an XAMP fanboy myself) ... I have got a sneaky suspicion that what you are asking of you current setup is impossible... though would be happy to be proved wrong ;)

---

### Post by Krauser Joestar on 2011-05-04
> **satanselbow said:**
> May be not quite the solution you are looking for but it may be simpler (and a hell of a lot quicker to implement);

Why not use a shared folder as your webroot and run a localserver on your W7 host pointed to the same location? Installing WAMP on W7 doesn't take long to set up (not an XAMP fanboy myself) ... I have got a sneaky suspicion that what you are asking of you current setup is impossible... though would be happy to be proved wrong ;)

I appreciate any type of help.

The thing is, i really want to do this in linux if there's any way to do it.

If there's not, then i will have to do what you said.

---

### Post by Krauser Joestar on 2011-05-04
Anyone ? :(

---

### Post by Krauser Joestar on 2011-05-04
bumping to keep the thread alive.

---

### Post by satanselbow on 2011-05-04
Just another :D idea but have you hit the Virtualbox forums to see if you can unravel the IP issues you've got - it might be a better place to find a Vbox networking guru ;)

I do feel you pain and would be interested in the answer myself :popcorn:

---

### Post by Krauser Joestar on 2011-05-04
That's a good idea, thanks satanselbow.

---

### Post by a2j on 2011-05-04
if both machines are on the same network, you should be able to ping/connect. if not, then you need a router in between those networks. otherwise, how else you're gonna get it to work?

---

### Post by satanselbow on 2011-05-04
That is rather the point a2j - I'm half convinced it can be done but required tweaking vbox settings / config that are out of my remit ;)

---

