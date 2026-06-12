---
title: "Allowing ports in ufw"
date: 2010-03-14
forum: General Help
---

### Post by Miyavix3 on 2010-03-14
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

I followed this tutorial about setting up a firewall and this all worked fine but when I try to add my own ports, they just don't work.

I try to add messenger protocols (aim, msn, etc...) so I find out what protocol they're using and add them to the list. After they're added to the list, they won't connect to their respective servers.

Should I add them to tcp, udf, or both? I set them to both.

Edit: I also have gufw installed and it hasn't really made a difference.

[Ubuntu 9.10 32bit]

---

### Post by Slim Moe on 2010-03-14
Um, better don't mess with the interfaces.

```
sudo ufw limit 80

```.. will allow limited inbound and outbound traffic on port 80 ( http ).

---

