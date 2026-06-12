---
title: "Open port Ktorrent"
date: 2010-03-18
forum: General Help
---

### Post by Lonnie82 on 2010-03-18
Hi,

Im using Ktorrent but the download speed is incredibly slow. I tried opening my port by using the following command:

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
But when scanning to see if the port is open I get a message saying it isn't responding.

Does anybody know how to open up the port and hopefully make the downloading faster?

Lonnie

---

### Post by Enigmapond on 2010-03-18
In my experience, allowing the port in iptables doesn't do much as iptables will allow it anyway if it's in response to your outgoing request. If you are behind a router, I would suggest forwarding the port there as that's where it will make a difference. At least this is what worked for me but with transmission, not Ktorrent.

---

### Post by Lonnie82 on 2010-03-19
Hi,

Thanks for the quick response. I'm really not great at this whole computer thing, could you perhaps explain to me how to forward the port?

Lonnie

---

### Post by claracc on 2010-03-19
I use ktorrent without speed problems except in the archives with little seeds and leechers.

To say ubuntu firewall to open the port 6881 I use the gufw, the gui frontend for ufw firewall (it is in the repositories, so you can install with synaptic). After installation, it is in system, firewall settings, write your password, and you add a rule: Simple tab, let both 6881, close window and the port is open to share the torrent files

---

### Post by Lonnie82 on 2010-03-23
Hi,

Thanks, that helped.

---

