---
title: "Send packets From A-B-C"
date: 2011-06-15
forum: General Help
---

### Post by mandreou86 on 2011-06-15
hello, im new in this forum. I m trying to sends packets from pc A to pc C through pc B. (A->B->C)
Pc B  use the command sysctl -w net.ipv4.ip_forward=1 ---> to forward the packets.

Pc A.Im using tcpdump to see the traffic.its ok. Only once.
Pc B.Im using tcpdump to see the traffic.I see every packet send twice from A to C, While I can see each packet to send only once from A to C. Why is this happening?
Pc C use tcpdump for the traffic.its ok. Only once

---

### Post by iponeverything on 2011-06-15
what's the topology? B is probably sending ICMP redirects.

---

### Post by mandreou86 on 2011-06-15
> **iponeverything said:**
> what's the topology? B is probably sending ICMP redirects.

I think B is in different switch. The packets pass through B but B receives each packet twice.
When i had the B in the same switch was sending ICMP redirects.

---

