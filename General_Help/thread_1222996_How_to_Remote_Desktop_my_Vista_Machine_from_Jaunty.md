---
title: "How to Remote Desktop my Vista Machine from Jaunty AMD64"
date: 2009-07-25
forum: General Help
---

### Post by Maya_Iz on 2009-07-25
I have read several posts but have not yet found a solution to this problem.

I have been able to connect remotely via my Vista Home boot to my Vista machine at work but have not yet been able to do so using rdesktop version 1.6 or TSClient. 

After 2 days of searching, I finally got the VPN Client to connect using kvpnc and just need to remote desktop the pc. 

I have even gone on youtube and watched a tutorial on TSClient (the tutorial was for RD to XP however) to make sure that I was following the proper procedures. Can anyone help me?

---

### Post by sanderj on 2009-07-25
I believe Vista Home has no option to receive rdesktop sessions.

See here: [http://ipv6-or-no-ipv6.blogspot.com/2009/05/help-needed-remote-desktop-from-ubuntu.html](http://ipv6-or-no-ipv6.blogspot.com/2009/05/help-needed-remote-desktop-from-ubuntu.html)

---

### Post by Maya_Iz on 2009-07-25
My PC at work is running Vista Business.

.

---

### Post by Scotty Bones on 2009-07-25
sanderj is correct. There is no remote desktop option for the home versions of XP and vista. Your best bet is probably VNC (over SSL recomended for security). I have had to do this before. If your ISP uses dynamic IP addressing, you will need a service like DynDNS or no-ip.

---

### Post by Maya_Iz on 2009-07-25
OK, maybe I am not making any sense. I have a dual boot option on my PC at home (the one that I want to use to RD to my work PC). I want to RD my work PC, running VISTA BUSINESS. Using my home PC (Vista Home), I can RD the PC at work. I want to be able to RD to the job PC from Jaunty (AMD64).

---

### Post by Scotty Bones on 2009-07-25
OK, I got ya now. TSclient should be the way to go. The problem is the protocols have changed from xp to vista. You will have to make sure that your user (on the business machine) will accept a connection from the older 2000/2003 protocol.



EDIT:
Now that I've had the opportunity to check my system. You should find the proper setting under..
System Properties> Remote. and select the radio button that states "Allow connections from computers running any version of Remote Desktop (less secure).
so forget the specific user deal.

---

### Post by Maya_Iz on 2009-07-26
But my work PC is already step to that.

---

### Post by Scotty Bones on 2009-07-26
Ok, lets step back for a second here and see if we can isolate the cause. Are you able to, using ubuntu, connect to any other remote server? If yes, then the issue is on the work side; If no, then it's on the home side. Then we can take it from there.

Also, double check to make sure that rdesktop is installed on your ubuntu machine. As TSclient is just the front-end.

---

### Post by sanderj on 2009-07-26
> **Maya_Iz said:**
> My PC at work is running Vista Business.

.

And how do you connect from your home vista to your work vista? A Remote Desktop session over plain Internet, or do you have to start a VPN?
Which command do you use?

If you use a plain Internet connection from Windows to Windows, what happens if you use "rdesktop <windows-at-work-IP-address>" on Ubuntu?

---

### Post by Scotty Bones on 2009-07-26
sanderj,
I am assuming (yeah, I know what they say about assumption), from the information in the first post, that his vista to vista connection is using plain internet; and his attempt at using a VPN (which he stated to be successful) being an after thought in getting ubuntu to connect.

---

### Post by Maya_Iz on 2009-07-27
I have no idea whether or not I can access any other remote server. Is there something that I can do to test it? 

I installed rdesktop on my machine as well. I thought that maybe I am not using it properly.

---

### Post by Maya_Iz on 2009-07-27
Sanderj,

In order to connect from my Vista, I first start a VPN (info can be found @ [http://cites.illinois.edu/vpn/]("http://cites.illinois.edu/vpn/")). I absolutely could not get it to work using Network Manager and after two days of trying, I finally tried KVpnc and it connected immediately (although the only way I can disconnect is by rebooting since none of the "Disconnect" buttons work).

When I run the command (after connecting to the VPN), I get the following:
> maya@maya-laptop:~$ rdesktop 128.174.190.25
Autoselected keyboard map en-us
ERROR: 128.174.190.25: unable to connect


---

### Post by sanderj on 2009-07-27
> **Maya_Iz said:**
> Sanderj,

In order to connect from my Vista, I first start a VPN (info can be found @ [http://cites.illinois.edu/vpn/]("http://cites.illinois.edu/vpn/")). I absolutely could not get it to work using Network Manager and after two days of trying, I finally tried KVpnc and it connected immediately (although the only way I can disconnect is by rebooting since none of the "Disconnect" buttons work).

When I run the command (after connecting to the VPN), I get the following:

After you've connected to the VPN, can you run on your local machine:
```
ifconfig
mtr 128.174.190.25
```

and post the output here. We need that info to see if you have a *working* VPN connection

On [http://cites.illinois.edu/vpn/otherclients.html](http://cites.illinois.edu/vpn/otherclients.html) it is said you need a PPTP connection as a VPN. Ubuntu can do that. However, let's first see what you have achieved yourself by isssueing the ifconfig and mtr command.

---

### Post by Maya_Iz on 2009-07-27
Here is what I got after running an "ifconfig"
> maya@maya-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:96:71:ce  
          inet addr:63.252.66.56  Bcast:63.252.67.255  Mask:255.255.254.0
          inet6 addr: fec0::8:21e:68ff:fe96:71ce/64 Scope:Site
          inet6 addr: 2002:3ffc:425f:8:21e:68ff:fe96:71ce/64 Scope:Global
          inet6 addr: fe80::21e:68ff:fe96:71ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7529309 (7.5 MB)  TX bytes:35840281 (35.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13706 (13.7 KB)  TX bytes:13706 (13.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.17.144.214  P-t-P:192.17.144.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1532 (1.5 KB)  TX bytes:72 (72.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:b5:20:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-68-B5-20-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Here after mtr 128.174.190.25
>                              My traceroute  [v0.75]
maya-laptop (0.0.0.0)                                  Mon Jul 27 20:07:15 2009
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. hh-gw.flexabit.net                0.0%    46   25.3   4.2   0.9  64.9  10.4
 2. CHCGILWUH53JC04-SO4-2-0-0.mcleod  0.0%    46    3.6   3.8   3.4   4.2   0.2
 3. equinix-chinng.abilene.ucaid.edu  0.0%    46    5.6   6.4   4.3  16.1   3.2
 4. 710rtr-i2cps.ex.ui-iccn.org       0.0%    46    5.1   5.1   4.5   6.0   0.4
 5. t-ur2rtr.ix.ui-iccn.org           0.0%    46    7.5   7.9   7.2  12.4   0.8
 6. iccn-ur2rtr-uiuc2.gw.uiuc.edu     0.0%    46    7.8  12.9   7.1 213.0  30.2
 7. 130.126.0.73                      2.2%    46    7.2   8.0   7.1  13.6   1.1
 8. ???


---

### Post by Maya_Iz on 2009-07-27
> **sanderj said:**
> After you've connected to the VPN, can you run on your local machine:
```
ifconfig
mtr 128.174.190.25
```

and post the output here. We need that info to see if you have a *working* VPN connection

On [http://cites.illinois.edu/vpn/otherclients.html](http://cites.illinois.edu/vpn/otherclients.html) it is said you need a PPTP connection as a VPN. Ubuntu can do that.

I tried and tried and tried and never got it working in Network Manager. KVpnc worked immediately, however, there is a bug b/c once I connect, I can only disconnect by rebooting. I'd be glad to have your advice on doing this in Network Manager (after we solve the first problem of course).

---

### Post by sanderj on 2009-07-28
@ifconfig:
You have a PPP session (good!) and the PPP session has IP address 192.17.144.214, which is owned by "University of Illinois" (see [http://whois.domaintools.com/192.17.144.214](http://whois.domaintools.com/192.17.144.214)), so that's good too.
Conclusion: it looks like a good VPN connection.

@mtr:
I can't see whether that route goes over the PPP connection. Check: which IP is reported by [http://whatismyipaddress.com/](http://whatismyipaddress.com/) ?
I can't check whether it's normal that you can't reach the destination machine. Can you check while running Windows as a client (tracert ...)?

And: are you sure the work Vista machine is running Remote Desktop service? I am not a Windows expert, but I believe that by default Vista runs another service.
Straight check: connect a Ubuntu machine (a live-CD boot is OK), next to your work Vista to the work LAN, and see whether you can connect. That way, there is no VPN involved. If that does not work either, the VPN is *not* the root cause.

---

### Post by Maya_Iz on 2009-07-28
> **sanderj said:**
> 
@mtr:
I can't see whether that route goes over the PPP connection. Check: which IP is reported by [http://whatismyipaddress.com/](http://whatismyipaddress.com/) ?
I can't check whether it's normal that you can't reach the destination machine. Can you check while running Windows as a client (tracert ...)?

And: are you sure the work Vista machine is running Remote Desktop service? I am not a Windows expert, but I believe that by default Vista runs another service.
Straight check: connect a Ubuntu machine (a live-CD boot is OK), next to your work Vista to the work LAN, and see whether you can connect. That way, there is no VPN involved. If that does not work either, the VPN is *not* the root cause.

Here is tracert from my Home Windows box:
> [FONT="System"]Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Maya>tracert 128.174.190.25

Tracing route to mntl3327-01.micro.uiuc.edu [128.174.190.25]
over a maximum of 30 hops:

  1     8 ms     8 ms     8 ms  vpn3.near.uiuc.edu [192.17.144.3]
  2     8 ms     8 ms     9 ms  uiuc-vpn3-net.gw.uiuc.edu [192.17.144.1]
  3    17 ms     8 ms     9 ms  t-dist1-1.gw.uiuc.edu [172.20.20.237]
  4     9 ms    10 ms     9 ms  t-bd-micro.gw.uiuc.edu [172.20.21.15]
  5     9 ms     8 ms     9 ms  mntl3327-01.micro.uiuc.edu [128.174.190.25]

Trace complete.

C:\Users\Maya>[/FONT]

Bizarre, the IP address from my Windows boot is 
192.17.144.239; however, when I switch back to my Ubuntu boot and connect the VPN, the IP address is different-63.252.66.56. This is the same IP address when I am not connect to the VPN.

Also, I take my laptop to work with me and connect via LAN on my Ubuntu boot all of the time since the wireless isn't so great in that area. I usually connect in a different room but on the same floor. I have never connected via LAN in the same room as the PC that I want to access remotely.

---

### Post by Maya_Iz on 2009-07-28
By the way, I am now at work and when I connect and rdesktop 128.174.190.25, it connects without a problem.

---

### Post by sanderj on 2009-07-28
> **Maya_Iz said:**
> By the way, I am now at work and when I connect and rdesktop 128.174.190.25, it connects without a problem.

With Ubuntu, I presume? That makes me think it's a VPN-problem, not a rdesktop-problem.

So focus on the VPN, and it's routing. I believe you showed different routes for the VPN on Ubuntu versus the VPN on Windows. That's strange, I would say, and has to be explained/solved. First check, on Ubuntu: is the traffic to the work windows routed over the VPN ... ?

---

### Post by Maya_Iz on 2009-07-28
Yes, with Ubuntu. How do I check that? I actually don't think that it is. I believe that the routing is the problem.

---

### Post by sanderj on 2009-07-29
> **Maya_Iz said:**
> Yes, with Ubuntu. How do I check that? I actually don't think that it is. I believe that the routing is the problem.

So that's exactly my idea: the problem is the networking, possibly not routing onto the VPN. It's not in rdesktop.

The first thing that strikes me, is that the windows-vpn-traceroute is completely over .edu routers, whereas the Ubuntu-vpn-mtr is over all kinds of non-.edu systems. So, things to check:
- On ubuntu, don't setup the PPTP-VPN, and do the same mtr. Check whether it's different than the Ubuntu-mtr you posted earlier. If *not*, the routing over your VPN is not working.
- On Ubuntu, with no PPTP-VPN working, type 'route'. Then, start the PPTP-VPN, and type 'route' again. *All* traffic should be routed over the VPN.

Question: how did you setup your PPTP-VPN on Ubuntu? BY a GUI-tool, or by hand-editing config files? It could be that there is a PPTP-VPN, but there is no routing onto that PPTP-VPN.


Example of my route working on my laptop via WLAN (with no VPN):
```
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
ubuntu@ubuntu:~$
```

---

### Post by Maya_Iz on 2009-07-29
Here is what I get when I run the route command before and after connecting.

[FONT="System"]> maya@maya-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
63.252.66.0     *               255.255.254.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         hh-gw.flexabit. 0.0.0.0         UG    0      0        0 eth0
maya@maya-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vpn3.near.uiuc. hh-gw.flexabit. 255.255.255.255 UGH   0      0        0 eth0
vpnmgt.gw.uiuc. *               255.255.255.255 UH    0      0        0 ppp0
63.252.66.0     *               255.255.254.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         hh-gw.flexabit. 0.0.0.0         UG    0      0        0 eth0
maya@maya-laptop:~$ [/FONT]

I found this [http://www.craigmayhew.com/blog/2009/07/fixing-ubuntu-9-04-vpn-adding-remote-network-to-routing-table/](http://www.craigmayhew.com/blog/2009/07/fixing-ubuntu-9-04-vpn-adding-remote-network-to-routing-table/) but cannot try it because the vpn doesn't connect in network manager.

---

### Post by rannable on 2009-07-29
No need, in Vista just enable remote desktop (Control Panel\System\Remote Settings) and from Ubuntu you should be able to connect straight to it using Terminal Services Client.
Failing that installing VNC on both will work too but this option is the simplest...

---

### Post by Maya_Iz on 2009-07-29
> **rannable said:**
> No need, in Vista just enable remote desktop (Control Panel\System\Remote Settings) and from Ubuntu you should be able to connect straight to it using Terminal Services Client.
Failing that installing VNC on both will work too but this option is the simplest...

Please read above that I have already done that.

---

### Post by sanderj on 2009-07-31
> **Maya_Iz said:**
> Here is what I get when I run the route command before and after connecting.

[FONT="System"][/FONT]

I found this [http://www.craigmayhew.com/blog/2009/07/fixing-ubuntu-9-04-vpn-adding-remote-network-to-routing-table/](http://www.craigmayhew.com/blog/2009/07/fixing-ubuntu-9-04-vpn-adding-remote-network-to-routing-table/) but cannot try it because the vpn doesn't connect in network manager.


In both cases you have the same default gateway, which is probably your DSL/cable connection. So, with the PPTP-VPN setup, you have to point your *default* route to the PPTP-VPN gateway. Google how to do that; it's something like 'sudo route add <gateway>', but I don't know the details. You have to remove the current default gateway from the 'route' settings.

HTH

---

### Post by sanderj on 2009-08-04
@OP

Have you tried the sudo route add default commands?

---

