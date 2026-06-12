---
title: "Tor stops bootstrapping at 25% because of time error, time settings not changing"
date: 2009-12-13
forum: General Help
---

### Post by Gitykins on 2009-12-13
```
neil@neil-desktop:~/tor-0.2.1.20$ tor
Dec 13 14:29:43.208 [notice] Tor v0.2.1.20. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Dec 13 14:29:43.208 [notice] Configuration file "/usr/local/etc/tor/torrc" not present, using reasonable defaults.
Dec 13 14:29:43.209 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Dec 13 14:29:43.209 [notice] Opening Socks listener on 127.0.0.1:9050
Dec 13 14:29:43.210 [notice] Parsing GEOIP file.
Dec 13 14:29:44.235 [warn] Our clock is 1 hours, 30 minutes behind the time published in the consensus network status document (2009-12-13 21:00:00 GMT).  Tor needs an accurate clock to work correctly. Please check your time and date settings!
Dec 13 14:29:44.327 [notice] I learned some more directory information, but not enough to build a circuit: We have no recent network-status consensus.
Dec 13 14:29:44.328 [notice] Bootstrapped 5%: Connecting to directory server.
Dec 13 14:29:44.444 [notice] Bootstrapped 10%: Finishing handshake with directory server.
Dec 13 14:29:46.231 [notice] Bootstrapped 15%: Establishing an encrypted directory connection.
Dec 13 14:29:46.494 [notice] Bootstrapped 20%: Asking for networkstatus consensus.
Dec 13 14:29:46.606 [notice] Bootstrapped 25%: Loading networkstatus consensus.
Dec 13 14:29:50.370 [warn] Our clock is 2 hours, 30 minutes behind the time published in the consensus network status document (2009-12-13 22:00:00 GMT).  Tor needs an accurate clock to work correctly. Please check your time and date settings!
Dec 13 14:29:50.370 [notice] I learned some more directory information, but not enough to build a circuit: We have no recent network-status consensus.
```

When I try to open time and date from Menu>System>Time and Date, I get this error:

```
The configuration could not be loaded

An unknown error occured.
```

---

