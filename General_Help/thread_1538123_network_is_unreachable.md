---
title: "network is unreachable"
date: 2010-07-24
forum: General Help
---

### Post by cpeachey on 2010-07-24
Ubuntu 32bit 10.04
Terminal ping 192.168.1.1 ""
192.168.1.1 is my router.
What have I done? I have 2 machines connected to the router with rj45 cables, this one connects ok the other one has suddenly stopped!
The last thing I did was installed "Picassa" (a photo album program) and also ran the latest update manager.
I don't seem to have a firewall installed, (at least I cannot see one listed as installed)
Any offers please?#-o#-o
Chris

---

### Post by sanderj on 2010-07-24
What's the output of 'ifconfig'?

---

### Post by wired99 on 2010-07-24
Are you running the same operating system on both?
Can you browse the internet from both?

I have read many tutorials on setting-up Samba but they have never worked for me.
However I do recommend that you do a quick Samba search on the forum.

I have however been able to make a direct connection between Ubuntu and Windows 7 by creating a "Launcher" in Ubuntu and a "Shortcut" in Windows using the corresponding ip address as the location.

Under Ubuntu - "Location: smb://ip.of.windows.machine"
Under Windows - "Target: \\ip.of.Ubuntu.machine"

---

### Post by cpeachey on 2010-07-24
The problem is that one pc cannot connect to anything! Both are connected to the same router but one, although the connection light is lit on the back of the pc and also on the router, is not connecting. A ping test says network is unreachable...there ere no ping times. So the problem is within the pc, either hardware or software.
If no-one can offer any solution I will try re-installing the operating system
Chris

---

### Post by Morbius1 on 2010-07-24
> Terminal ping 192.168.1.1 ""I'm sorry, but does that mean you can't ping the router?

If you go to the working machine can you access the router and find out if it can see both machines?

---

### Post by cpeachey on 2010-07-24
Output of ifconfig as follows...

chris@ubuntu2:~$ sudo ifconfig 
[sudo] password for chris: 
eth0      Link encap:Ethernet  HWaddr 44:87:fc:51:78:56  
          inet6 addr: fe80::4687:fcff:fe51:7856/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5217 (5.2 KB)  TX bytes:1184 (1.1 KB) 
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 

chris@ubuntu2:~$

---

### Post by cpeachey on 2010-07-24
1 machine can ping the router and connect to the internet but cannot ping the 2nd machine.(destination host unreachable)
The 2nd machine cannot ping the router so cannot connect to anything. 
Chris

---

### Post by sanderj on 2010-07-24
> **cpeachey said:**
> Output of ifconfig as follows...

chris@ubuntu2:~$ sudo ifconfig 
[sudo] password for chris: 
eth0      Link encap:Ethernet  HWaddr 44:87:fc:51:78:56  
          inet6 addr: fe80::4687:fcff:fe51:7856/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5217 (5.2 KB)  TX bytes:1184 (1.1 KB) 
          Interrupt:27 Base address:0x2000 

chris@ubuntu2:~$

So: no IP address on your ethernet connection. Is the ethernet cable plugged in on both sides, and is the (yellow?) LED on?

If so, in Ubuntu, in the right upper corner, if you right-click with your mouse, what are the settings? Is Wired Networking enabled? Under IPv4 settings, is DHCP on?

---

### Post by cpeachey on 2010-07-24
Ethernet cable is plugged in. The yellow light is on and the router shows a connection on that port is on.
IPv4 "Automatic DHCP"
Network Connections/wired/Auto eth0 last used "never"
I note that on the machine that DOES work ok ...Network Connections/wired...there is no entry at all.

---

### Post by cpeachey on 2010-07-24
On the duff machine
looking at system/administration/network tools/Devices/network device/ethernet interface eth0 IPv6 has a mac address but IPv4 has zeros
Have I deleted this (IP address) somehow? an if so how do I put it back?
Chris

---

### Post by sanderj on 2010-07-24
> **cpeachey said:**
> On the duff machine
looking at system/administration/network tools/Devices/network device/ethernet interface eth0 IPv6 has a mac address but IPv4 has zeros
Have I deleted this (IP address) somehow? an if so how do I put it back?
Chris

The IPv6 is probably a FE80: address, right? If so, it's a self assigned IPv6 address, and no proof of an ethernet connection.

---

### Post by sanderj on 2010-07-24
If you live-boot a Ubuntu CD, does the ethernet connection work then? If so, it's a software/setting problem.

---

### Post by cpeachey on 2010-07-24
IPv6 is a FE80 etc address.
I will try the CD route tommorrow. Thanks for your help.
Chris

---

