---
title: "Apache2 is not connecting to the Internet"
date: 2009-08-11
forum: General Help
---

### Post by Unisaga on 2009-08-11
I wasn't sure where to post this so I put it in general help.

Basically my problem is that after i've installed Apache2, MySQL, and PHP5, I can't access my site via the Internet (through my IP address). I was able to set up a server quite awhile back (last year sometime) but I don't recall what I had to fix to make it work. Something isn't letting it connect to the Internet and I am not sure what it is. I am currently on wireless Internet via my home router on a DSL connection (about 3 Mbps). Does anyone have any suggestions or ideas as to why I can't access my server through my ip address. It shows up fine locally. Could it be my router? Or that I am trying to do it from a wireless connection?

---

### Post by credobyte on 2009-08-11
Port forwarding ( [http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding) ) should fix your problem ;)

---

### Post by Unisaga on 2009-08-11
I've already forwarded port 80 for my laptop, and 81, but it still doesn't show up. Are there any others that I might need?

---

### Post by wojox on 2009-08-11
You need to port forward port 443 https is on by default.

---

### Post by giggins on 2009-08-11
Here's a quick checklist of things to make sure you have for this to work (not in any particular order):

1) Port forwarding (you said this is done)
2) Static IP on the server (if the IP changes, then port forwarding is broken)
3) If you're using a firewall on the server, make sure its allowing connections to that port from anywhere.
4) Make sure apache2 is listening on all interfaces (or at least the interface attached to your router's internal network. This is the default on a new apache2 install though the .deb package)
5) Can you get to the server from a browser on itself? (You said this works, right?)
6) Can you get to the server from the internal network? (the one behind the router, not including on the server itself).

Still not working? Some ISPs don't allow home users to host sites on normal ports. Try setting it up to listen on a port above (or including) 1024.

---

### Post by cariboo on 2009-08-11
Check [canyouseeme]("http://www.canyouseeme.org/") to make sure the ports you have forwarded are open to the rest of the world.

---

