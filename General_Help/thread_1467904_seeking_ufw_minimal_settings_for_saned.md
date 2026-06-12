---
title: "seeking ufw minimal settings for saned"
date: 2010-05-01
forum: General Help
---

### Post by meonkeys on 2010-05-01
I run a saned daemon on an Ubuntu 9.10 server, and use xsane clients on other machines. Does anyone know a secure way to open up the server's firewall to allow access to a scanner? I'm looking for the minimum amount of ports I can open up.

I tried "sudo ufw allow from 10.1.1.0/24 to any port saned", but this doesn't work. I'm guessing xsane needs to hit some more ports on the server or something.

---

### Post by meonkeys on 2010-12-01
Saned needs some high ports open, I guess. See data_portrange in /etc/sane.d/saned.conf. I made that range 20300-20900, then opened those ports for TCP and UDP traffic. This, in addition to the "sane-port" (6566) made it work!

---

### Post by genaoufe on 2011-01-10
> **meonkeys said:**
> I run a saned daemon on an Ubuntu 9.10 server, and use xsane clients on other machines. Does anyone know a secure way to open up the server's firewall to allow access to a scanner? I'm [[COLOR=#000000]looking[/COLOR]](http://www.tekbar.net/fr/cost-and-investment/cost-and-investment172.html) for the minimum amount of ports I can open up.I tried "sudo ufw allow from 10.1.1.0/24 to any port saned", but this doesn't work. I'm guessing xsane needs to hit some more ports on the server or something.It's good for reference, This is what I'm looking for, Thanks for your effort!

---

