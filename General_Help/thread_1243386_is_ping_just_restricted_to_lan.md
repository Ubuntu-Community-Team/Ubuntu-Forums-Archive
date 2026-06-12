---
title: "is ping just restricted to lan??"
date: 2009-08-18
forum: General Help
---

### Post by abhilashm86 on 2009-08-18
if i ping my own username, i will get result and ip adress and by nmap, can any of  hostname in internet world can be knew by use of ping...........

---

### Post by Grenage on 2009-08-18
Yes, you can ping any **host**name provided it's in your hostfile or resolvable by DNS.  Also provided your ISP does not block ICMP, and the other end doesn't drop the ICMP packets (firewall).

---

### Post by wojox on 2009-08-18
No you can ping Google, yahoo etc...
Some site can deny ping results as well.

---

### Post by credobyte on 2009-08-18
You can ping whatever you want, however, some hosts may deny these requests ( even Firestarter have this option .. ICMP filtering ).

---

### Post by abhilashm86 on 2009-08-18
oh i got it, is ping principle and operation both other OS like MS and mac, using ip adress is better to ping or hostname? 
yes most websites allow ping and some don't:)

---

### Post by credobyte on 2009-08-18
> **abhilashm86 said:**
> oh i got it, is ping principle and operation both other OS like MS and mac, using ip adress is better to ping or hostname? 
yes most websites allow ping and some don't:)

What exactly you are trying to achieve ? nslookup & host would perform better in case if you want to get server info :)

---

### Post by abhilashm86 on 2009-08-18
> **credobyte said:**
> What exactly you are trying to achieve ? nslookup & host would perform better in case if you want to get server info :)

yes i want inforamtion and properties of host computer or server, just learning now about networks, what are alterantive softwares do you recommend?

---

