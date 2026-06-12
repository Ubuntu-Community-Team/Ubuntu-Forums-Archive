---
title: "How to check my NIC is working or not..."
date: 2009-12-26
forum: General Help
---

### Post by emigrant on 2009-12-26
hi all,
i have a Speedcom+ 4 port Router. I used to connect it with ethernet. My
internet connection was disconnected for about 2 months and after
reconnecting when i try to use the router it won't work. the LAN LED
won't flash and the light in NIC port also won't flash. if i take the
router to one of my friends pc then it works fine.
 
how can i find the fault?
how do i know whether the problem is in router or NIC?
 
thank you very much
this is an attachement of my network connections.
if i select the 'auto etho' that search thing keeps rotating but never gets connected.

---

### Post by jonest1 on 2009-12-26
There are a couple things I would do.

First, try a different network cable.  If the one you have is bad, what you are seeing would be the cause.

Next, I know this doesn't sound promising, but try to configure the network card with an IP address and not dhcp.  Make sure the IP address and subnet mask match your current network.  Try to ping or connect to the router.

Other options are to look for errors in your log files /var/log/messages and dmesg.

Run ifconfig and verify your network card is eth0 and is not in an UP state.  Try running '/etc/init.d/networking restart' and see if the output can give a clue as to the problem and check the messages log file after this command as well.

---

### Post by emigrant on 2009-12-26
thank you very much for your reply.
latest update,
after i restarted the router, now auto eth0 not shwoing up :confused:
> **jonest1 said:**
> There are a couple things I would do.

First, try a different network cable.  If the one you have is bad, what you are seeing would be the cause.


tried with 3 cables. all work when at friends house, not working at my home.
> **jonest1 said:**
> 
Next, I know this doesn't sound promising, but try to configure the network card with an IP address and not dhcp.  Make sure the IP address and subnet mask match your current network.  Try to ping or connect to the router.

please how to do this?

> **jonest1 said:**
> 
Other options are to look for errors in your log files /var/log/messages and dmesg.
 

```
$ dmesg | tail
[  474.512016] usb0: no IPv6 routers present
[  559.750227] PPP BSD Compression module registered
[  559.752617] PPP Deflate Compression module registered
[  693.581955] UDF-fs: No VRS found
[  693.652195] ISO 9660 Extensions: Microsoft Joliet Level 3
[  693.693606] ISOFS: changing to secondary root
[ 1722.632736] r8169: eth0: link up
[ 1722.632920] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1733.008507] eth0: no IPv6 routers present
[ 2573.946144] r8169: eth0: link down
```



> **jonest1 said:**
> 
Run ifconfig and verify your network card is eth0 and is not in an UP state.  Try running '/etc/init.d/networking restart' and see if the output can give a clue as to the problem and check the messages log file after this command as well.
 [/quote]

```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:af:6e:4f  
          inet6 addr: fe80::2e0:4dff:feaf:6e4f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3546 (3.5 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6724245 (6.7 MB)  TX bytes:6724245 (6.7 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.200.242.49  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:6807367 (6.8 MB)  TX bytes:2263929 (2.2 MB)

usb0      Link encap:Ethernet  HWaddr 02:80:37:14:03:00  
          inet6 addr: fe80::80:37ff:fe14:300/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:168 (168.0 B)
```

```
$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface ppp0=ppp0.

```

---

### Post by jonest1 on 2009-12-26
From your output of ifconfig, it looks like you may have once had a adsl type connection over usb (ppp0 and usb0).  I'm not sure if this is causing some of the issues, but you can manually configure the eth0 interface through network manager.

If you do not have a ppp0 interface, you may want to delete it, but that would be a secondary troubleshooting step.  I'm a little concerned the ppp0 link is coming up with an IP address and is listed as UP.  

This link on the Ubuntu wiki is very useful.
[https://help.ubuntu.com/9.10/internet/C/index.html](https://help.ubuntu.com/9.10/internet/C/index.html)

More specifically, this link gives the information on how to manually configure a network interface.
[https://help.ubuntu.com/9.10/internet/C/connecting-wired.html](https://help.ubuntu.com/9.10/internet/C/connecting-wired.html)

You may want to go to the IPv6 tab and set that to Ignore as well if it is not already.

---

### Post by dcstar on 2009-12-27
> **emigrant said:**
> hi all,
i have a Speedcom+ 4 port Router. I used to connect it with ethernet. My
internet connection was disconnected for about 2 months and after
reconnecting when i try to use the router it won't work. the LAN LED
won't flash and the light in NIC port also won't flash. if i take the
router to one of my friends pc then it works fine.
 
how can i find the fault?
how do i know whether the problem is in router or NIC?


If the router works elsewhere but not on your PC then the PC or the cable is faulty.

Boot off a Live CD and see if the connection then works.

---

### Post by emigrant on 2009-12-27
hi the problem here is,
i have tested with three cables and it all works fine at friends home but not with my pc.
and at my home i can't even get to the router config page :192.168.1.1 (it worked perfectly at friends home with the same cables).
and the dsl light in the router is keep blinking without keep flashing.

i couldn't figure out where the problem is :confused:

---

### Post by CharlesA on 2009-12-27
NIC card is probably toast then, since you said that there is no activity light on either the NIC or the router.

It's either that or the NIC isn't "on."

But boot off a livecd and see if it works. If it does, then it's a config problem.

---

### Post by cascade9 on 2009-12-27
> **CharlesA said:**
> NIC card is probably toast then, since you said that there is no activity light on either the NIC or the router.

It's either that or the NIC isn't "on."

But boot off a livecd and see if it works. If it does, then it's a config problem.

It is possible that the netword card is turned 'off' in BIOS, but I would gess the OP would remember doing that. 

There is a good chance that its toast.

---

### Post by emigrant on 2009-12-27
i checked in BIOS. but it seems all ok. may i know any specifi place there i should look with bit careful?

why does the network manager shows three types of connections while i can connect only to mobile broadband?

please see the attachement.
the top one had a radio button earlier today, but after a reboot now its also not there.

all confusing :confused:

edit: booting from live cd did'nt make a change.

---

