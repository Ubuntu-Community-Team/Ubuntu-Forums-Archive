---
title: "iptables dns go through lo !?"
date: 2012-04-28
forum: General Help
---

### Post by Frozen Forest on 2012-04-28
Recently installed ubuntu 12.04 and was going to use the same iptables rules as I did in the previous version, but for some unknown reason won't the dns work. For some reason does outgoing dns requests pass through the loopback interface, this will cause the package to be dropped. Why does it go through loopback? It's even the outgoing request.

[PHP]
iptables -N dns-chain
iptables -A dns-chain -p udp --sport 53 --dport 1024:65535 -j accept-in
iptables -A dns-chain -p udp --sport 1024:65535 --dport 53 -j accept-out
iptables -A INPUT -j LOG $LOG_DROP "In: "
iptables -A INPUT -p udp --sport 53 --dport 1024:65535 -j dns-chain
iptables -A OUTPUT -p udp --sport 1024:65535 --dport 53 -j dns-chain
[/PHP][PHP]
In: IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=19630 DF PROTO=UDP SPT=37196 DPT=53 LEN=63 
[/PHP]

---

