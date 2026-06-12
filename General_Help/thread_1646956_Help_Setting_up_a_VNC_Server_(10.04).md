---
title: "Help Setting up a VNC Server (10.04)"
date: 2010-12-16
forum: General Help
---

### Post by Torombolo on 2010-12-16
I tried google, and forum search but i just cant seem to find it.

I want to set up a VNC connection from another network to my PC, ive done it Localy with no probs, but i just cant figure out how to do it from another Network.




Thanks in advance.

---

### Post by altjx on 2010-12-16
> **Torombolo said:**
> I tried google, and forum search but i just cant seem to find it.
 
I want to set up a VNC connection from another network to my PC, ive done it Localy with no probs, but i just cant figure out how to do it from another Network.
 
 
 
 
Thanks in advance.
 
Have you port forwarded correctly if you're behind a router?

---

### Post by Torombolo on 2010-12-16
> **altjx said:**
> Have you port forwarded correctly if you're behind a router?



i havent checked that, was just talking about that with a college at work.... how ironic..


Since i have 2 routers in the same connection (1 is not wireless) i have port em both right?

---

### Post by Slim Odds on 2010-12-16
> **Torombolo said:**
> i havent checked that, was just talking about that with a college at work.... how ironic..


Since i have 2 routers in the same connection (1 is not wireless) i have port em both right?

Not sure what you mean, but the bottom line is that you need a route from one PC to the other. For an IP connection, that means and address and a port. Since your PC is not directly connected to the Internet, you'll need to forward the proper port(s) from the router to your PC.

If you're talking about over the Internet, you'd better be very careful about security. Personally, I'd tunnel the connection through and ssh session.

A simple diagram of your network would be very helpful.

---

### Post by joberly on 2010-12-16
> **Torombolo said:**
> 

Since i have 2 routers in the same connection (1 is not wireless) i have port em both right?


You only need to port forward on the router that is facing the internet, as you should not have both routers doing NAT. One of them should be in bridged mode.

---

### Post by Torombolo on 2010-12-16
My network is like this :

2Wire Router, Linkys is connected to the 2wire via Ethernet. from the linksys 2 Hardwired Desktops, 2 Iphones and 1 Pc wireless.

---

### Post by Slim Odds on 2010-12-17
> **Torombolo said:**
> My network is like this :

2Wire Router, Linkys is connected to the 2wire via Ethernet. from the linksys 2 Hardwired Desktops, 2 Iphones and 1 Pc wireless.

Is the Linksys being used as a router or just a hub?

Wouldn't really make sense to have double routers. Anyway, your 2Wire is the one connected to the Internet, right? To connect to a computer on your network from the Internet, you'll have to know the global IP address that your 2Wire is getting from your internet provider. Then you'll need to forward whatever ports that you need on to the local computer.

Like I warned before, there are some serious security issues related to doing this. I highly recommend that you read up and learn more about it.

---

### Post by Torombolo on 2010-12-17
Worked, did not have to change my Pc to the main network, worked well with the linksys.

Now i just need to add individual ports for the other PCs.


Im Reading about the Security Risks.


Thanks you again.

Edit.

Manage to Add Individual ports.

---

