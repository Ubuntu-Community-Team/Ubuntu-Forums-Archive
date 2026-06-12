---
title: "pidgin no longer connects to jabber servers"
date: 2011-10-17
forum: General Help
---

### Post by wolxXx on 2011-10-17
hey community!

first: sorry for my bad english, i'm trying my best :)

now here's my problem: since the upgrade to 11.10, i could not connect to the jabber servers i used before. i run an own server, he is alive, friends of me could connect...
but when i try to connect, i got this error message: "Der Server benutzt keine der unterstützten Authentifizierungsmethoden" which means, that the server does not support the auth methods.. 
what i did to try to solve this problem: 
- i deleted the recieved certificates in .purple/certificates/x509/tls_peers -> i got new ones from the server -> no change, still won't connect
- connected with gajim -> wonderfull fast connection, everything perfect
- tried to create a new account on my own and on jabber.ccc.de server -> same as above -> server does not supports methods

so what should i do now? can anybody help me please? thanks alot!

---

### Post by m00ny on 2012-12-09
Hi,
for all, who find this post, like me: you need to have correct entrys in /etc/hosts and /etc/hostname

---

