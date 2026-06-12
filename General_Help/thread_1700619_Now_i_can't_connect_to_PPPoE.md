---
title: "Now i can't connect to PPPoE"
date: 2011-03-05
forum: General Help
---

### Post by rva1945 on 2011-03-05
Yesterday I bought a netbook and a wifi router (TP-Link), I connected the ADSL modem to the router, then the router (output) to the ehternet in the desktop with U 9.10. I configured the router to dial the modem.

The router dials the modem, the modem connects, and I have wifi at home, the netbook (still with W7) connects to the wifi network. So far so good.

BUT now the Ubuntu in the desktop doesn't connect. No netwok. If I run sudo pppoeconf, after a scanning process it says that probably there's another pppoe proccess that is controlling the modem. I guess it tries to dial.

PLS HLP

Later, when I install U 10.10 in the notebook I'll have to struggle with the wifi network...but that will be another story...

---

### Post by gandaran on 2011-03-05
> **rva1945 said:**
> Yesterday I bought a netbook and a wifi router (TP-Link), I connected the ADSL modem to the router, then the router (output) to the ehternet in the desktop with U 9.10. I configured the router to dial the modem.

The router dials the modem, the modem connects, and I have wifi at home, the netbook (still with W7) connects to the wifi network. So far so good.

BUT now the Ubuntu in the desktop doesn't connect. No netwok. If I run sudo pppoeconf, after a scanning process it says that probably there's another pppoe proccess that is controlling the modem. I guess it tries to dial.

PLS HLP

Later, when I install U 10.10 in the notebook I'll have to struggle with the wifi network...but that will be another story...
if the router is doing the dialing why are you using 'sudo pppoeconf'?
check that the dchp server is enabled in the router and that network is enabled in the network manager icon, also if you have any previous wired ethernet setup connection in network manager remove them as it mite not allow the detection of the new one.

---

### Post by rva1945 on 2011-03-05
> **gandaran said:**
> if the router is doing the dialing why are you using 'sudo pppoeconf'?
check that the dchp server is enabled in the router and that network is enabled in the network manager icon, also if you have any previous wired ethernet setup connection in network manager remove them as it mite not allow the detection of the new one.

Well, I ran pppoeconf just because I didn't know what else to do.
the router is a TPlink

Firmware Version:         3.11.7 Build 100603  Rel.56412n 
                       Hardware Version:         WR741N v1/v2 00000000

The DHCP is enabled 

start ip 192.168.1.100
end ip 192.168.1.199
default gateway  192.168.1.1

default domain is in blank
primary dns 0.0.0.0
secondary dns 0.0.0.0
In Ubuntu, the networking is enabled, there's only one connection, under Wired tab, 

ifupdown  (eth0) and the delete button is disabled (I guess it was automatically created when i installed U 9.10).

---

### Post by rva1945 on 2011-03-05
> **gandaran said:**
> if the router is doing the dialing why are you using 'sudo pppoeconf'?
check that the dchp server is enabled in the router and that network is enabled in the network manager icon, also if you have any previous wired ethernet setup connection in network manager remove them as it mite not allow the detection of the new one.


I created another connection, automatically IP DHCP, the problem was, there were the two old DNS, deleted them, re-started Ubuntu...voilaa!! It's connected.

Thanks.

BTW: the netbook has W7 and a workgroup, in order to use the printer which is connected to the Desktop Ubuntu 9.10, what can I do?

Does it work if I set the workgroup to the same name in Ubuntu? Or it only works with Windows workgroups?

---

### Post by gandaran on 2011-03-05
> BTW: the netbook has W7 and a workgroup, in order to use the printer which is connected to the Desktop Ubuntu 9.10, what can I do?

Does it work if I set the workgroup to the same name in Ubuntu? Or it only works with Windows workgroups?
I don't know about W7 but in XP all I do is set up a network workgroup to open the firewall then I would find the printer in networks, on the ubuntu side I just enable the publish and show shared printers options.

---

