---
title: "Equivalent of ipconfig"
date: 2009-07-08
forum: General Help
---

### Post by james.brantley on 2009-07-08
[SIZE=2]Could someone tell me the equivalent of ipconfig for the Ubuntu command line? Thanks!

edit: it appears ifconfig gives me some data.
[/SIZE]

---

### Post by iponeverything on 2009-07-08
What is it your trying to do?

---

### Post by james.brantley on 2009-07-08
> **iponeverything said:**
> What is it your trying to do?

[SIZE=2]I needed to verify the ip address assigned to my wireless router it was conflicting with a new dsl modem that was assigned the same address as the router. 
 They were both 192.168.1.1, when entered that took me to the modem configuration page and I was unable to access the router config page. [/SIZE][SIZE=2]After a reset of the modem I was able to log in to the router. [/SIZE][SIZE=2]I changed the router address to 192.168.2.1 after that no more conflicts and I can access both devices if need be. [/SIZE][SIZE=2]
[/SIZE]

---

### Post by t4thfavor on 2009-07-08
I usually try to use a 10.x.x.x network when for my internal stuff as there are way too many conflicts with the 192.168.x.x networks.

My cable modem did this as well, So I just blocked private IP's from accessing the WAN, and it went away.

---

### Post by james.brantley on 2009-07-08
> **t4thfavor said:**
> I usually try to use a 10.x.x.x network when for my internal stuff as there are way too many conflicts with the 192.168.x.x networks.

My cable modem did this as well, So I just blocked private IP's from accessing the WAN, and it went away.

[SIZE=2]That sure would resolve it wouldn't it? Thank for the insight.

[/SIZE]

---

