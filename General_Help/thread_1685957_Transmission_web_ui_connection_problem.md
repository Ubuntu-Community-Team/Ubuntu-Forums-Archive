---
title: "Transmission web ui connection problem"
date: 2011-02-11
forum: General Help
---

### Post by mealstrom on 2011-02-11
Hi, ive got some problem:

Ive got ubuntu 10.04 x64 server with transmision-daemon transmission-common installed
(ive tried both from rep and from source code). 
torrent service is up:
[PHP]
netstat -plutn | grep 9091
tcp        0      0 0.0.0.0:9091            0.0.0.0:*               LISTEN      9487/transmission-d
[/PHP]it was working good for about half a day, a can connect to it from WAN and now, when im home - i cant connet from LAN.  It just didnt respond

[PHP]telnet server 9091 
Escape character is '^]'.
GET /index.htm HTTP/1.1
and nothing.
[/PHP][PHP]cat /var/log/syslog | grep transmission
Feb 11 17:08:49 dreamguard transmission-daemon[9487]: Saved "/var/lib/transmission-daemon/info/stats.json" (bencode.c:1683)
this message every 10 mins[/PHP]

whitelist is off. 

Only service restart solves the problem.

Any idea?

---

### Post by mealstrom on 2011-02-16
Look's like problem was solved in 2.21

---

