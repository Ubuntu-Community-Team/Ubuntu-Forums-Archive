---
title: "Good server firewall?"
date: 2011-04-20
forum: General Help
---

### Post by Dustin2128 on 2011-04-20
I'm getting my first web server configured, and as per a tutorial I found, I used shorewall. However, it blocks all internet access (even from apt) to my server! Does anyone know a decent firewall program or a good guide on configuring shorewall?

---

### Post by lisati on 2011-04-20
Many modern routers have firewall capabilities, and can be configured relatively painlessly through their web interface. The trick is to only allow incoming connections through ports that your server is likely to be listening to, e.g. 80 for a website and 25 for incoming email.

Having said that, there's nothing wrong with investigating your options, as you seem to be doing with tools like shorewall.

---

