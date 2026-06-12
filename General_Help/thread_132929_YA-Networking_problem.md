---
title: "YA-Networking problem"
date: 2006-02-19
forum: General Help
---

### Post by smarri on 2006-02-19
I am posting this because I am at my wits end. To start, let me say that I am a complete newcomer to Linux. I choose Ubuntu because I regularily saw it being recommended as a good friendly starting linux. So far it has been an enjoyable experience and I have found the forums here a great resource. Anyway, enough preamble!

I have been having this problem since I first installed Ubuntu(5.10 plus update manager updates). Basically, I can connect to the internet but it seems to randomly drop the connection and I have to go to the network panel to deactivate and reactivate my wired network card on EN0.

Some info about the system, if this helps. 

The wired network card is built into the motherboard. It is an intel 10/100 network card. Shows up as :82801BA/BAM/CA/CAM Ethernet.

I have a Wireless card plugged into one of my PCi slots. Although this shows up in the Device Manager panel, it does not show anywhere else. At the moment it is not a priority to get this working, I mention it only in case it may be causing some clash or confilct with the wired card.

The daemon log shows this when the connection is dropped then re-established:

```
Feb 19 13:57:54 localhost dhclient: receive_packet failed on eth0: Network is down
Feb 19 13:57:56 localhost dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6279
Feb 19 13:57:56 localhost dhclient: removed stale PID file
Feb 19 13:57:56 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 19 13:57:56 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 19 13:57:56 localhost dhclient: All rights reserved.
Feb 19 13:57:56 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Feb 19 13:57:56 localhost dhclient: 
Feb 19 13:57:56 localhost dhclient: sit0: unknown hardware address type 776
Feb 19 13:57:56 localhost dhclient: sit0: unknown hardware address type 776
Feb 19 13:57:56 localhost dhclient: Listening on LPF/eth0/00:03:47:9c:dc:2c
Feb 19 13:57:56 localhost dhclient: Sending on   LPF/eth0/00:03:47:9c:dc:2c
Feb 19 13:57:56 localhost dhclient: Sending on   Socket/fallback
Feb 19 13:58:00 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 19 13:58:00 localhost dhclient: DHCPACK from 10.70.0.1
Feb 19 13:58:00 localhost dhclient: bound to 80.0.***.*** -- renewal in 235439 seconds.

```

(Edited 80.0.*.* IP address)

Any help with this will be much appreciated. As you can imagine it is quite aggravating having to constantly disable and re-enable the network card through longer downloads!

Simon

---

