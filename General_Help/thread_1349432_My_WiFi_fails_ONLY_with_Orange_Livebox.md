---
title: "My WiFi fails ONLY with Orange Livebox"
date: 2009-12-08
forum: General Help
---

### Post by Lockheed on 2009-12-08
I just moved and now I have to use Orange Livebox as my wireless router.
The problem is, it just does not work under Linux.

In windows, I connect stright away and have normal pings to router and internet.

In ubuntu, it either does not connect at all, or when it does, I get pings like 8000 or 33000 when I try to ping the router but no internet at all. This is how the ping looks like if I am lucky enough to establish a connection:

```
$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=2692 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=2401 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=1919 ms
64 bytes from 192.168.1.254: icmp_seq=7 ttl=64 time=6313 ms
64 bytes from 192.168.1.254: icmp_seq=8 ttl=64 time=6024 ms
64 bytes from 192.168.1.254: icmp_seq=9 ttl=64 time=5740 ms
64 bytes from 192.168.1.254: icmp_seq=10 ttl=64 time=5048 ms
64 bytes from 192.168.1.254: icmp_seq=18 ttl=64 time=7080 ms
64 bytes from 192.168.1.254: icmp_seq=19 ttl=64 time=6494 ms
64 bytes from 192.168.1.254: icmp_seq=20 ttl=64 time=6201 ms
64 bytes from 192.168.1.254: icmp_seq=21 ttl=64 time=5213 ms
64 bytes from 192.168.1.254: icmp_seq=22 ttl=64 time=4214 ms
64 bytes from 192.168.1.254: icmp_seq=23 ttl=64 time=3509 ms
64 bytes from 192.168.1.254: icmp_seq=24 ttl=64 time=3022 ms
64 bytes from 192.168.1.254: icmp_seq=25 ttl=64 time=3458 ms
64 bytes from 192.168.1.254: icmp_seq=26 ttl=64 time=3381 ms
64 bytes from 192.168.1.254: icmp_seq=27 ttl=64 time=7700 ms
64 bytes from 192.168.1.254: icmp_seq=28 ttl=64 time=7519 ms
64 bytes from 192.168.1.254: icmp_seq=29 ttl=64 time=6729 ms
64 bytes from 192.168.1.254: icmp_seq=30 ttl=64 time=7359 ms
64 bytes from 192.168.1.254: icmp_seq=31 ttl=64 time=8817 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

```

I have newest WICD and everything is up to date as well. My card is Atheros on ath5 or ath9 (can't remember) and I never had such problems on any other WEP, WPA, WPA2 network.

Any ideas?

---

