---
title: "cant browse net while connected to both lan and wlan"
date: 2011-08-13
forum: General Help
---

### Post by loolooyyyy on 2011-08-13
i am connected to my wireless router (wlan0)
i'm also connected to my laptop via cable (eth0)
wlan0 has the internet connection, if i disconnect eth0 i can browse internet but if it's connected, i cant
eth0 has manual address: 192.168.0.7
wlan: auto (right now:182.168.0.255)
what should i do?
and please do not tell me to google it, i have

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> i am connected to my wireless router (wlan0)
i'm also connected to my laptop via cable (eth0)
wlan0 has the internet connection, if i disconnect eth0 i can browse internet but if it's connected, i cant
eth0 has manual address: 192.168.0.7
wlan: auto (right now:182.168.0.255)
what should i do?
and please do not tell me to google it, i have

you need to manipulate routing table.

[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by loolooyyyy on 2011-08-13
tanx for the quick reply but now i'm totally confused!
what exactly should i do?

---

### Post by haqking on 2011-08-13
your routes (gw addresses) need to point to your ethernet lan for eth0

and routes for internet to point to wlan0

but you need to have static ip addresses on both

---

### Post by loolooyyyy on 2011-08-13
great, i dont have my wireless router's ip address and it seems i cant find it out, the router itself in it's configuration page just gives the ip for LAN not WLAN
and this is the ifconfig output:

eth0      Link encap:Ethernet  HWaddr 60:eb:69:70:23:9b  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe70:239b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103751 (103.7 KB)  TX bytes:176874 (176.8 KB)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57638 (57.6 KB)  TX bytes:57638 (57.6 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f3:95:e6:d9:e6  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f3:95ff:fee6:d9e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9628849 (9.6 MB)  TX bytes:2615044 (2.6 MB)

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> great, i dont have my wireless router's ip address and it seems i cant find it out, the router itself in it's configuration page just gives the ip for LAN not WLAN
and this is the ifconfig output:

eth0      Link encap:Ethernet  HWaddr 60:eb:69:70:23:9b  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe70:239b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103751 (103.7 KB)  TX bytes:176874 (176.8 KB)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57638 (57.6 KB)  TX bytes:57638 (57.6 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f3:95:e6:d9:e6  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f3:95ff:fee6:d9e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9628849 (9.6 MB)  TX bytes:2615044 (2.6 MB)


from your wlan0 connection ping your router.  If you can see its config page then you must know its IP address

192.168.0.1 by the looks of it

thing is you are using class 192.168.0 for both eth and wireless

---

### Post by loolooyyyy on 2011-08-13
wow this is going on great here thanks to haqking
yes it's ip was the default: 192.168.0.1
sorry for acting so dumb, but what do i do next?

---

### Post by loolooyyyy on 2011-08-13
ok firefox works perfectly after
```
sudo route add default gw 192.168.0.1 wlan0
```
but ping doesnt, ant ideas?

when i ssh from laptop to pc now it says:
ssh: connected to host 192.168.9.5 port 22: No route to host
:(

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> wow this is going on great here thanks to haqking
yes it's ip was the default: 192.168.0.1
sorry for acting so dumb, but what do i do next?


remember not to post multiple threads which you have done, as it is now confusing.

[http://ubuntuforums.org/showthread.php?t=1824219](http://ubuntuforums.org/showthread.php?t=1824219)

---

### Post by loolooyyyy on 2011-08-13
no haqking i'm not making multiple threads
that one was for fixing my uncles network
this is for fixing my own!

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> ok firefox works perfectly after
```
sudo route add default gw 192.168.0.1 wlan0
```but ping doesnt, ant ideas?

when i ssh from laptop to pc now it says:
ssh: connected to host 192.168.9.5 port 22: No route to host
:(


ok good thats the oringal problem sorted then.

what do you want to ping ?

where is the 192.168.9.5 that is a different network to yours ?

---

### Post by d3v1150m471c on 2011-08-13
why do you need to be connected to a cat5 cable and wireless? why not just connect to one or the other?

---

### Post by loolooyyyy on 2011-08-13
the things are now like this:
pc connected to router
router ip: 192.168.0.1 - pc ip on wlan: 192.168.0.2
and did this:
router add default gw 192.168.0.1 wlan0

firefox=>works
ping google.com =>now works (suddenly!)

on pc - ip of eth0 set to: 192.168.9.5 (since you said both having 192.168.0 was making problems)

BUT
ssh from laptop to pc:
ssh user@192.168.9.5
```
ssh: connect to host 192.168.9.5 port 22: No route to host
```

---

### Post by loolooyyyy on 2011-08-13
i'm trying to run xdmx to use laptop's monitor as a second monitor my pc is connected to internet via wireless
(actually it's not a pc, they are both laptops that one of them is old and does not have wireless, i called the new one pc here to prevent confusion)
(ps; the old laptop has intel graphics new one ati)

the situation is a little more complex:
i ssh to pc from laptop, start Xdmx blablabla, says: no module fglrx
i tried to find the solution on net, but hey! whlie the cable is connected i cant surf net, now tanx to haqking problem now fixed

now i cant ssh

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> the things are now like this:
pc connected to router
router ip: 192.168.0.1 - pc ip on wlan: 192.168.0.2
and did this:
router add default gw 192.168.0.1 wlan0

firefox=>works
ping google.com =>now works (suddenly!)

on pc - ip of eth0 set to: 192.168.9.5 (since you said both having 192.168.0 was making problems)

BUT
ssh from laptop to pc:
ssh user@192.168.9.5
```
ssh: connect to host 192.168.9.5 port 22: No route to host
```

so your other PC is on 192.168.9.x also ?

and have you added a route for that network ?

and yes as above said , why do you need both connections ?

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> i'm trying to run xdmx to use laptop's monitor as a second monitor my pc is connected to internet via wireless
(actually it's not a pc, they are both laptops that one of them is old and does not have wireless, i called the new one pc here to prevent confusion)
(ps; the old laptop has intel graphics new one ati)

the situation is a little more complex:
i ssh to pc from laptop, start Xdmx blablabla, says: no module fglrx
i tried to find the solution on net, but hey! whlie the cable is connected i cant surf net, now tanx to haqking problem now fixed

now i cant ssh

so you also have a thread about xdmx at [http://ubuntuforums.org/showthread.php?t=1824200](http://ubuntuforums.org/showthread.php?t=1824200)

all these questions should be in one thread

---

### Post by d3v1150m471c on 2011-08-13
i think... wlan0 and eth0 == same local area network. no need for all the complexity. Have the pc connected by either wlan0 or eth0 not both, and do the same from your laptop. I would recommend setting up static ip's on your router if you planning on "ssh'ing" to the pc because on dhcp you will have to run and check the remote pc's ip all the time if it changes. it could also change and kill your ssh sessions, too. both systems should be able to access icannet by a single lan connection if your lan is connected to the internet. I have a similar setup using ubuntu desktop and a ubuntu vps. I have dhcp disabled on the router and i have limited assignable addresses that are specific to each machine's mac address with wpa wireless protection. it keeps out most idiots and keeps things super simple. if i want to ssh 2 my vps then i have a simple script i run with port knocking to connect to the vps at the same address everytime. might want to make sure ssh is running on your remote host, and also, make sure it's not blocking you from the firewall.

---

### Post by loolooyyyy on 2011-08-13
like i said for xdmx
cable for xdmx, wireless router for internet

in network-manager-applet i set "auo eth0" ip to "192.168.9.5" - i left auto WLAN-NAME to automatic (DHCP)
i added the route for wlan0
now firefox works, ping works, ssh gives that error

the laptop doesnt have wireless, just lan, and through it, it's connected to pc,  and it doesnt need to be connected to internet at all, i just want to use it's monitor

---

### Post by d3v1150m471c on 2011-08-13
> **loolooyyyy said:**
> 
the laptop doesnt have wireless, just lan, and through it, it's connected to pc,  and it doesnt need to be connected to internet at all, i just want to use it's monitor

wireless != lan. wlan0 == wireless interface, eth0 == ethernet (cat5) interface. lan == local area network. wlan0 and eth0 are two different interfaces to connect to the same lan, so **no need to connect with both**. this could very well be why you're having routing problems, too.

---

### Post by haqking on 2011-08-13
> **d3v1150m471c said:**
> wireless != lan. wlan0 == wireless interface, eth0 == ethernet (cat5) interface. lan == local area network. wlan0 and eth0 are two different interfaces to connect to the same lan, so no need to connect with both. this could very well be why you're having routing problems, too.


ha ha join me in my confusion ;-)

i lost a grip of this about 10 minutes ago...LOL

---

### Post by loolooyyyy on 2011-08-13
i was calling the eth0 lan because this manual here did!
sorry

so everything looks like this jpeg here: [ATTACH]199981[/ATTACH]

i need the wlan0 to be connected to internet
i need the eth0 to connect my laptop to pc

just change the lan word in the picture to eth0 youself, thank you

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> i was calling the eth0 lan because this manual here did!
sorry

so everything looks like this jpeg here: [ATTACH]199981[/ATTACH]

i need the wlan0 to be connected to internet
i need the eth0 to connect my laptop to pc

just change the lan word in the picture to eth0 youself, thank you


your laptop is on DHCP and not static and on a different network of 192.168.**0**.99 and your Eth0 on your PC is on 192.168.**9**.5

---

### Post by loolooyyyy on 2011-08-13
exactly, i set the laptop to 192.168.9.99 and now everything works just fine
thanks to you haqking, again[U]
[/U]

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> exactly, i set the laptop to 192.168.9.99 and now everything works just fine
thanks to you haqking, again

ok so all, solved now ?

if so mark the thread as solved from thread tools. cheers

---

### Post by d3v1150m471c on 2011-08-13
you should still consider setting your router to assign static ip addresses...
ie:
 192.168.1.1 == router (gateway)
 192.168.1.2 == laptop
 192.168.1.3 == pc

it will save you much trouble in the future.

---

