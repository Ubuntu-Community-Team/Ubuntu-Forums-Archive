---
title: "network problem"
date: 2010-03-06
forum: General Help
---

### Post by bs1126 on 2010-03-06
Hey guys!
I have my second machine with linux. First one with ethernet conection.
It's a celeron 800mhz with 256mb that runs pretty fine ^^
Here is what I have:
A lynksys WRT54G conected to my ISP via ethernet, and I have a computer  on wireless and two via cable: the computer that I'm writing right now  with windows xp sp3 and the other one with ubuntu 9.04.
Cable conections seems to be right, the green light on router is on, and  in the back of the pci card on the ubuntu pc, is on too.
As I said the ubuntu pc have a PCI Card....I looked up which was and its  a SIS900 PCI Fast Ethernet (rev 83).
Tried several thing. I modified the /etc/network/interfaces several  times with no results at all. Tried to get on system/preferences/network  conections and I see this "auto eth0" and don't know how to figured  out. 
Tried some things on terminal....executed pppoeconf and said  to me that i'm not conected.
Other thing that I tried so far:
```
tomas@tomas-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit URL

Listening on LPF/eth0/00:d0:09:c3:a2:40
Sending on   LPF/eth0/00:d0:09:c3:a2:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Also when I click on the network icon on desktop shows me "Wired  Network: disconected" [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG]
If someone could help me, I appreciate so much!

---

### Post by lars.thornqvist@pdahl.se on 2010-04-19
Ciao! Did you find any solution to this? I have the same issue after upgrading to ubuntu 9.10 :(

---

### Post by alphacrucis2 on 2010-04-19
> **bs1126 said:**
> Hey guys!
I have my second machine with linux. First one with ethernet conection.
It's a celeron 800mhz with 256mb that runs pretty fine ^^
Here is what I have:
A lynksys WRT54G conected to my ISP via ethernet, and I have a computer  on wireless and two via cable: the computer that I'm writing right now  with windows xp sp3 and the other one with ubuntu 9.04.
Cable conections seems to be right, the green light on router is on, and  in the back of the pci card on the ubuntu pc, is on too.
As I said the ubuntu pc have a PCI Card....I looked up which was and its  a SIS900 PCI Fast Ethernet (rev 83).
Tried several thing. I modified the /etc/network/interfaces several  times with no results at all. Tried to get on system/preferences/network  conections and I see this "auto eth0" and don't know how to figured  out. 
Tried some things on terminal....executed pppoeconf and said  to me that i'm not conected.
Other thing that I tried so far:
```
tomas@tomas-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit URL

Listening on LPF/eth0/00:d0:09:c3:a2:40
Sending on   LPF/eth0/00:d0:09:c3:a2:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Also when I click on the network icon on desktop shows me "Wired  Network: disconected" [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG]
If someone could help me, I appreciate so much!

What does 

```
sudo ethtool eth0
```

return?

---

### Post by slooksterpsv on 2010-04-19
Hmmm odd looks like the subnet its finding is 255.255.255.255 which only gives you 1 usable IP.

Have you tried setting your IP information statically or power-cycling your router?

---

### Post by alphacrucis2 on 2010-04-19
> **slooksterpsv said:**
> Hmmm odd looks like the subnet its finding is 255.255.255.255 which only gives you 1 usable IP.

Have you tried setting your IP information statically or power-cycling your router?

Isn't that just the DHCP broadcast? It doesn't know a subnet at that point.

From DHCP wiki:

[QUOTE="Wiki"]This client-implementation creates a User Datagram Protocol (UDP) packet with the broadcast destination of **255.255.255.255** or the specific subnet broadcast address.[/QUOTE]

The real problem is that the DHCP broadcasts are not getting a response.

---

### Post by slooksterpsv on 2010-04-19
> **alphacrucis2 said:**
> Isn't that just the DHCP broadcast? It doesn't know a subnet at that point.

Holy crap read that totally wrong above. You're right it's the DHCP broadcast. I must have read socket and eth0 together and thought it said subnet. Sorry.

==========
Have you tried a different ethernet cable?

---

### Post by trig on 2010-04-19
my brother havs that same pci Linksys card. He uninstantiated the card and placed it back in, rebooted and made sure the enmabling wirelesss button was checked and it got wireless right away.

---

### Post by lars.thornqvist@pdahl.se on 2010-04-19
Intresting...yep Im actually setting my ip manually;
 
192.168.0.51 / 255.255.255.0 / 192.168.1.0
 
Can't really see why it say 255.255.255.255
 
________________________
 
[EMAIL="lt@ubuntu:~$"]lt@ubuntu:~$[/EMAIL] [COLOR=red]**sudo dhclient eth0**
[/COLOR][sudo] password for lt: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:0c:29:86:a6:a9
Sending on   LPF/eth0/00:0c:29:86:a6:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.154.158 from 192.168.154.254
DHCPREQUEST of 192.168.154.158 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.154.158 from 192.168.154.254
bound to 192.168.154.158 -- renewal in 763 seconds.

[EMAIL="lt@ubuntu:~$"]lt@ubuntu:~$[/EMAIL] [B][COLOR=red]sudo dhclient eth1[/COLOR]
[/B]There is already a pid file /var/run/dhclient.pid with pid 1783
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth1/00:11:50:e7:7f:38
Sending on   LPF/eth1/00:11:50:e7:7f:38
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[EMAIL="lt@ubuntu:~$"]lt@ubuntu:~$[/EMAIL] 

 
___________________________________________________
 
Any ideá how to change the 255.255.255.255?? I have set it to 255.255.255.0 in my manual IP settings using the built in manager.

---

### Post by alphacrucis2 on 2010-04-20
> **lars.thornqvist@pdahl.se said:**
> Intresting...yep Im actually setting my ip manually;
 
192.168.0.51 / 255.255.255.0 / **192.168.1.0**



If you are setting a manual ip address then there is no point in running dhclient. Also the 192.168.1.0 - if that is meant to be the default gateway then that will never work. Please post the output of:

```
sudo ethtool eth0
sudo ethtool eth1
ifconfig
route -n
```

 
> Can't really see why it say 255.255.255.255

That is the normal broadcast address that the DHCP client uses to find a DHCP server.

---

