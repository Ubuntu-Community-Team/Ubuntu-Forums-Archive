---
title: "SSH Over Alternate Port Blocked?"
date: 2011-03-28
forum: General Help
---

### Post by steevven1 on 2011-03-28
So I have two ssh servers I connect to regularly that do not use the standard port 22, so I use the "-p" flag to connect to them. This works flawlessly EVERYWHERE except on my girlfriend's work network. When I am on that network (same laptop), I can ssh into servers which use port 22, but not the other servers on this alternate port.

Is there any way OTHER than ssh'ing into a machine I can access and then ssh'ing again from there to my destination (which, by the way, does work)? I want to make a direct connection for speed and security reasons.

Is the network I'm on blocking traffic on this port?

Thanks in advance!

---

### Post by Dark_Stang on 2011-03-28
The network is either blocking the port, or is blocking the ssh protocol. And yes, fancy routers are smart enough to detect and block certain protocols (some can even block based on content).

---

### Post by HermanAB on 2011-03-28
Howdy,

Use port 80 or 443.  Those are always open.

---

