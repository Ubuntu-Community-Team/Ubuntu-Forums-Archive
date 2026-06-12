---
title: "Modifying Protocol stack in Linux"
date: 2005-03-06
forum: General Help
---

### Post by pratikreal on 2005-03-06
Hi every1,

i am workin on a proj that requires me to modify TCP header of outgoing packets.

How do I get control over TCP headers? i tried modifying usr/src/linux2.4.20-8/net/ipv4/tcp_output.c

But it dint work... :(

Can any1 help me??

Waiting for a helpful reply...
Pratik

---

### Post by dignaciojr on 2008-06-17
> **pratikreal said:**
> Hi every1,

i am workin on a proj that requires me to modify TCP header of outgoing packets.

How do I get control over TCP headers? i tried modifying usr/src/linux2.4.20-8/net/ipv4/tcp_output.c

But it dint work... :(

Can any1 help me??

Waiting for a helpful reply...
Pratik
Hi guys,

as with the mentioned problem above, I also have the same problem now with my research. Following are my questions:

 The problem with me is " how do we insert a variable in option field of TCP header so that when I used TCP dump to capture packets, I can see that variable as well
Thank you heaps in advance

Cheers, dom

---

