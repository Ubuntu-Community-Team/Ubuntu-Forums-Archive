---
title: "need advice on my network connection"
date: 2006-06-06
forum: General Help
---

### Post by yellowband on 2006-06-06
Hi.
I'm desperate for some advice on my networking problem.  I was having trouble getting my computer on the network with windows so i switched to Ubuntu, thinking it was a windows-OS thing.  However, i cannot access the internet at all from my ubuntu machine.  here's a little list of where i'm at:

- i'm sure my internet connection is working, i have hooked up to it via ethernet from a windows-based laptop.
- I don't think it is the network card.  I tried both the network card on my motherboard, and i also tried one that i just installed (PCI).  The new card appears to be successfully installed as Ubuntu has recognized it and it shows up with the motherboard controller under the networking window in ubuntu.  
- I have tried goign through my router and hooking the ubuntu machine straight up to the modem. no luck here.
- I have tried activating/deactivating all the combinations of eth1/eth0 in the networking window but still no luck.  

I have little linux experience, but i am willing to try anything here.  Thank you.

---

### Post by professor_chaos on 2006-06-06
Under network settings you will find if you press the properties button, make sure its configured for you setting (fixed ip, dchp, etc)

You to see if you have some DNS issue, then should try and ping some address from the terminal. Open up a terminal and type ```
ping www.red.com
```
what happens?

---

### Post by yellowband on 2006-06-06
hi, thanks for the reply.

I checked the properties menu in the networking window and the eth1 and eth0 are set to DCHP (like they are suposed to).  I then opened the terminal and typed "ping www.red.com", and the response was:

ping: unknown host [www.red.com](www.red.com).

Also, i don't think it would matter since i have them both activated right now, but how do i know which eth0/eth1 is pointing to which network card?  i don't need the motherboard controller active since i'm not using it.

---

### Post by professor_chaos on 2006-06-06
the command ```
ifconfig
``` should tell you the configuration of each card.

---

### Post by yellowband on 2006-06-06
thanks,

any other reason why my internet connection is not working properly though?

---

### Post by yellowband on 2006-06-06
i couldn't really make use of any of the information that ifconfig gave me.  Any ideas at all to fix this?

---

