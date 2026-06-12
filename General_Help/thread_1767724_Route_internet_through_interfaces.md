---
title: "Route internet through interfaces?"
date: 2011-05-26
forum: General Help
---

### Post by redcodefinal on 2011-05-26
Hi,

I have an interesting problem for you all today. Lately, I've been learning a lot about computer security and I have a weird request. I would like to route the internet connection from a laptop running BackTrack 5 (Linux distrobution for security), to another Backtrack computer through an SSH session. I believe this is called SSH tunneling. Essentially I have these interfaces set up.

```

eth0
wifi0

```

I would like to route the internet I get from wifi0 and send it through eth0. Essentially this would make my laptop a sort of hub.

The reason is, I have a wireless router I use for all my penetration testing computers and I don't like them on my network normally. I want it so that way I can use my main computer, which has no wifi card, to connect to this network. Also, this would be great experience for other things.

I'm not completely set on having it done through an SSH session also. I think there is a way to do it with iptables but, I'm not entirely sure how. 

Thanks in advance!

-Ian

---

### Post by aeiah on 2011-05-26
i dont think you can do it through ssh alone, although if it is possible it'd probably be easier. 

a way to test would be:
on your computer that does not have a wifi card, ssh into your 'hub' computer. when logged in, can you ping your testing router? if it automatically bridges between eth0 and wifi0, then you can probably set up an ssh tunnel in a normal way.

if not, you'll have to look into IPtables, as you feared :p keywords to google for would be 'NAT' and 'masquerade', or perhaps instead of a full nat on your hub laptop, you can set up a bridge between eth0 and wifi0 (again using iptables). you may run into problems if you have DHCP as you may get your IP address from your normal router and end up on the wrong subnet.

---

