---
title: "strange network problem on 11.10"
date: 2011-11-25
forum: General Help
---

### Post by deserthowler on 2011-11-25
I upgraded from 11.04 to 11.10.  When I rebooted, I got the following messages on the splash screen:
[LIST]
[*]Waiting for network configuration ...
[*]Waiting up to 60 more seconds for network configuration ...
[*]Booting system without full network configuration ..
[/LIST]

Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02).  Ubuntu worked on this machine since 7.04.

Network-manager couldn't find either the wired or wireless connection.  I rebooted a couple of times with the same results.  

Fortunately I was using WICD on my 11.04 install so I deleted network-manager.  :)  I then opened WICD.  It found things immediately.  I picked my WiFi link.  I went on with my work on line.  Before I shut down, I enabled WICD in start up.  I still get that message on boot and it takes about a minute for WICD to find the network and connect.  Once connected the connection is solid and problem free.

I used 11.10 upgraded from 11.04 on this machine previously with no problems.  :confused:  I've upgraded continuously since 9.04 or 9.10 with no problems.

Earl

---

### Post by deserthowler on 2011-12-01
bump

---

