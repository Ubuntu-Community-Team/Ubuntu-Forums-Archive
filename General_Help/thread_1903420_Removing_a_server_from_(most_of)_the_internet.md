---
title: "Removing a server from (most of) the internet?"
date: 2012-01-02
forum: General Help
---

### Post by minchina on 2012-01-02
Using the new year as an excuse, I finally got around to re-tuning my home server running 10.04.3.  While it serves many important functions on my own home network, I realized that it needs to have very little interaction with the real, outside internet.  It needs to connect to the Ubuntu server for security updates, to my email provider to download new emails (for archiving purposes, which I could live without if it made this harder), and that's just about it.  

In light of this, and in the interest of securing it a bit more, I was wondering if there was a way to implement some sort of internet whitelist on the server.  Unless an (out of my network) site is on the whitelist, it simply will not connect or accept connections.

My question is twofold.  1) With this actually have any impact on the security of the server, or am I just deluding myself, and 2) Is this possible?  Just in case it is relevant, I'm running an unmodded linksys WRT router.

thanks.

---

### Post by Lars Noodén on 2012-01-02
You could use IP Tables to whitelist connections.  Be sure not to block essentials like DNS and ICMP.

The merits of such an endeavor are less certain.  I'd say there's very little return on the effort except maybe as a learning exercise.  Ubuntu is fairly secure out of the box and if your services need a firewall then they probably should not be on the net to begin with.

---

### Post by minchina on 2012-01-02
Thanks Lars.  If the benefits are limited and the "screw up the system by accidentally blocking DNS" potential is high, I think I will skip it for now.  I figured it was worth asking.

---

