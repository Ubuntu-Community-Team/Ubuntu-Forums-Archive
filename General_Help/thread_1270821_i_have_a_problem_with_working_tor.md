---
title: "i have a problem with working tor"
date: 2009-09-20
forum: General Help
---

### Post by alimolavi on 2009-09-20
Sep 20 11:32:57.646 [Notice] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Sep 20 11:32:57.647 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Sep 20 11:32:57.647 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 20 11:32:57.647 [Notice] Opening Control listener on 127.0.0.1:9051
Sep 20 11:32:57.647 [Notice] Parsing GEOIP file.
Sep 20 11:35:10.209 [Notice] Tried for 120 seconds to get a connection to [scrubbed]:1443. Giving up. (waiting for circuit)
Sep 20 11:38:57.058 [Warning] Problem bootstrapping. Stuck at 85%: Finishing handshake with first hop. (DONE; DONE; count 10; recommendation warn)
Sep 20 11:38:58.065 [Warning] Problem bootstrapping. Stuck at 85%: Finishing handshake with first hop. (DONE; DONE; count 11; recommendation warn)
Sep 20 11:39:10.114 [Warning] Problem bootstrapping. Stuck at 85%: Finishing handshake with first hop. (DONE; DONE; count 12; recommendation warn)
Sep 20 11:39:21.444 [Warning] Problem bootstrapping. Stuck at 85%: Finishing handshake with first hop. (Connection timed out; TIMEOUT; count 13; recommendation warn)
Sep 20 11:39:58.309 [Warning] Problem bootstrapping. Stuck at 85%: Finishing handshake with first hop. (DONE; DONE; count 14; recommendation warn)


i have no firewall and i check my time system

---

### Post by life-on-mars on 2009-11-23
You probably need a bridge to connect to a directory server. Open [https://bridges.torproject.org/](https://bridges.torproject.org/) or email [email]bridges@torproject.org[/email] (using gmail or yahoo to keep the bridges' IPs secret) with "get bridges" in the body of the mail and reconfigure Tor using the provided bridges.

If you cannot open that page because it is blocked, try to find a proxy (you might need to try several proxy before you find a working one).

You might want to install TorK to simplify configuration and have a nice GUI for Tor.

---

