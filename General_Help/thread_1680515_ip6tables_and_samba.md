---
title: "ip6tables and samba"
date: 2011-02-02
forum: General Help
---

### Post by earplugg on 2011-02-02
I recently set up a tunnel to tunnelbroker.met to use IPv6 at home, using my ubuntu server as gateway. After doing this my windows 7 computer started to lose connection to the servers samba share periodically. This is most noticeable when watching videos on the share from the win7 comp, every 3-4 minutes the video stops when the connection to the share is lost.   The problem seems to be caused by ip6tables, if I turn of ipv6 filtering samba works fine.

This is my ip6table rules:
```
Chain INPUT (policy DROP 2 packets, 160 bytes)
 pkts bytes target     prot opt in     out     source               destination
   75 36468 ACCEPT     all      any    any     anywhere             anywhere            ctstate RELATED,ESTABLISHED
  243 21816 ACCEPT     all      eth0   any     anywhere             anywhere
    0     0 ACCEPT     all      lo0    any     anywhere             anywhere

Chain FORWARD (policy DROP 20259 packets, 1102K bytes)
 pkts bytes target     prot opt in     out     source               destination
 2533  203K ACCEPT     all      eth0   any     anywhere             anywhere
  607 96322 ACCEPT     all      any    any     anywhere             2001:xxxx:xxxx:xxxx::/64 ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT 332 packets, 29878 bytes)
```My LAN, where the win 7 computer is located, is behind eth0 and I allow all traffic on that interface so I don't understand how these rules can affect samba, but if I set the input policy to ACCEPT samba works fine.

What have I missed?

---

