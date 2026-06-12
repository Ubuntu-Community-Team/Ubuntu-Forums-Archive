---
title: "Web site on the net"
date: 2010-01-14
forum: General Help
---

### Post by bobmac on 2010-01-14
Folks,

What do I need to install to have my web site recognised on the net. I've done it several times in Windows but I'm unsure of what I need in ubuntu. I assume that I need some sort of a server but again I'm unsure of what to do and, or, install.

Any help appreciated,

Bob

---

### Post by lisati on 2010-01-14
I have a basic setup for hosting a website:
[LIST=1]
[*]A free domain with [www.no-ip.com](www.no-ip.com)
[*]Apache running on my main desktop, with web pages stored in /var/www
[*]My routers set so that incoming requests to port 80 get through to my main desktop
[*]My modem/router set to keep no-ip automatically updated with my IP address so that it can do the DNS lookup thing. (no-ip offer software to do the update for you if your modem/router doesn't support this)
[/LIST]

[http://lisati.myftp.org](http://lisati.myftp.org) is hosted on one of my own machines.

---

