---
title: "Syncrify SSL issue"
date: 2011-05-29
forum: General Help
---

### Post by yrufset on 2011-05-29
Hello,
I installed Syncrify server and client on Ubuntu.
From what i read in their site, Syncrify comes with a built in Self-signed SSL certificate.
But after i set the SSL port on the Syncrify Admin Set-Up, 
i still can't login with a client through SSL.
This works:
[Http://host.com:5800](Http://host.com:5800) (5800 is default port for http)
But these:
[https://host.com:443](https://host.com:443)
[https://host.com](https://host.com)
Doesn't work....

Can anyone help me?

Thank!

---

### Post by yrufset on 2011-05-30
Well....
Ubuntu's default state is all ports are blocked.
Although firewall was turned off it seemed like it's still blocking incoming communication.
I turned it on and allowed port 443, and Voulla:
Everything works now.

---

