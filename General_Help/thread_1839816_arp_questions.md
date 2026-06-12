---
title: "arp questions"
date: 2011-09-06
forum: General Help
---

### Post by COKEDUDE on 2011-09-06
Can someone please explain this output to me. Why doesn't ifconfig show the same info? 

```
~ $ arp -a
? (10.71.0.1) at 00:1b:21:2b:eb:0c [ether] on eth0

```

---

### Post by haqking on 2011-09-06
> **COKEDUDE said:**
> Can someone please explain this output to me. Why doesn't ifconfig show the same info? 

```
~ $ arp -a
? (10.71.0.1) at 00:1b:21:2b:eb:0c [ether] on eth0

```


What is your ifconfig output ?

cant tell you unless you show us ;-)

I expect your arp output is that of your gateway on the eth0 lan.

Arp shows your neigbours on the lan, if only you and a router then it shows your router

---

### Post by The Cog on 2011-09-06
**ifconfig** will show you the MAC and IP addresses of th einterfaces on your computer. On the other hand, **arp -a** will show you the MAC and IP addresses of your computer's neighbours (that it has spoken to recently).

---

