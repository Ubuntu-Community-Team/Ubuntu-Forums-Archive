---
title: "Help installing Ubuntu Server 11.04"
date: 2011-08-01
forum: General Help
---

### Post by Jwag598 on 2011-08-01
So I decided to take my old computer and turn it into a server with Ubuntu Server 11.04. I'm following ItchyHippo's tutorials ([[COLOR=#444444]http://www.youtube.com/watch?v=e08uQ...el_video_title[/COLOR]]("http://www.youtube.com/watch?v=e08uQmw4MJU&feature=channel_video_title")). But during the install this always comes up: 
[CENTER]**Network Autoconfiguration failed**[/CENTER]
[LEFT]**Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly. **[/LEFT]
 
[LEFT]I'm using a qwest DSL Modem connected to a netgear FS105 Ethernet Switch, and my computer that I'm using as a server is connected to that from the port on the motherboard but I aslo have a internet card in there, its a netgear lc82c169c. The my mom's, brother's and my new computer are all connect to the switch without a problem.[/LEFT]
 
[LEFT]Also, I'm a complete newbie to all this[/LEFT]
 
[LEFT]Thanks in advance:smile:
 
Also when I type: **Sudo nano /etc/network/interfaces** I get this
 
# This file describes the network interfaces avaliable on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interfaces
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
         address 192.168.0.5
         netmask 255.255.255.0
         netwrok 192.168.0.0
         Broadcast 192.168.0.255
         gateway 192.168.0.1
         # dns-* options are implemented by the resolvconf package, if installed
         dns-nameservers 192.168.0.1
 
 
 
**Ifconfig: **
 
lo      Link encap:Local Loopback
         inet addr:XXX.X.X.X  Mask 255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:0 errors:0 Dropped:0 overruns:0frame:0
         TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
RX bytes:0(0.0 B)   TX byes (0.0 B)[/LEFT]

---

