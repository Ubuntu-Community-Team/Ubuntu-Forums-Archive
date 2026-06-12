---
title: "Traceroute not verbose :("
date: 2010-04-15
forum: General Help
---

### Post by dgrafix on 2010-04-15
How can i get tracerouter to tell me where it is going like the windows one?
All i get is a load of stars.

---

### Post by wojox on 2010-04-15
The stars usually indicate the router or machines between them are overloaded or down.
You get that on the whole screen?

---

### Post by dgrafix on 2010-04-17
If i tracert it from windows i get a proper trace, if i do it using traceroute all i get is 3 stars (repeating).

I can also access the sites i am trying to trace to.

I cannot even trace to my own router?! (which is working fine)
> ***@***-*****:~$ traceroute 192.168.1.1
traceroute to 192.168.1.1 (192.168.1.1), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *


---

### Post by gmargo on 2010-04-17
Do you have any firewall software configured?

---

