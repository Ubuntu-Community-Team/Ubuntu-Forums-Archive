---
title: "Probelm with Tor"
date: 2011-02-16
forum: General Help
---

### Post by cikson on 2011-02-16
I am running Portable Tor on Windows 7 in my office but  have problem with connection,  evidently problem is in McAfee firewall.  When I use option &#8220;My firewall only lets me connect to certain ports&#8221; &#8220;80&#8221; then message log is:```
vlj 16 13:58:54.817 [Notice] Tor v0.2.1.29 (r8e9b25e6c7a2e70c). This is experimental software. Do not rely on it for strong anonymity. (Running on Very recent version of Windows [major=6,minor=1]  [workstation] {terminal services, single user})
vlj 16 13:58:54.818 [Notice] Initialized libevent version 1.4.14-stable using method win32. Good.
vlj 16 13:58:54.818 [Notice] Opening Socks listener on 127.0.0.1:9050
vlj 16 13:58:54.818 [Notice] Opening Control listener on 127.0.0.1:23
vlj 16 13:58:54.818 [Notice] Parsing GEOIP file.
vlj 16 14:00:00.274 [Notice] No current certificate known for authority moria1; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority tor26; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority dizum; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority ides; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority gabelmoo; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority dannenberg; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority urras; launching request.
vlj 16 14:00:00.275 [Notice] No current certificate known for authority maatuska; launching request.
```
With option "My ISP blocks connections to the Tor network" &#8220;  212.186.99.12:9001
62.75.162.12:9001
92.255.166.137:443&#8221;, message log is: ```
vlj 16 14:04:39.904 [Notice] Tor v0.2.1.29 (r8e9b25e6c7a2e70c). This is experimental software. Do not rely on it for strong anonymity. (Running on Very recent version of Windows [major=6,minor=1]  [workstation] {terminal services, single user})
vlj 16 14:04:39.905 [Notice] Initialized libevent version 1.4.14-stable using method win32. Good.
vlj 16 14:04:39.905 [Notice] Opening Socks listener on 127.0.0.1:9050
vlj 16 14:04:39.905 [Notice] Opening Control listener on 127.0.0.1:23
vlj 16 14:04:39.905 [Notice] Parsing GEOIP file.
vlj 16 14:04:45.240 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 1; recommendation warn)
vlj 16 14:04:45.480 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 2; recommendation warn)
vlj 16 14:04:45.690 [Warning] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Socket is not connected [WSAENOTCONN ]; NOROUTE; count 3; recommendation warn)
``` 
How can I bypass firewall (I don't have admin. password)?
Please help!

---

