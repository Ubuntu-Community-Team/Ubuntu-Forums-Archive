---
title: "Ventrilo help..."
date: 2009-09-10
forum: General Help
---

### Post by Lyerae on 2009-09-10
Hi, I'm trying to get the Ventrilo server to run on Linux. I can connect using "127.0.0.1", but people cannot connect using my IP.
The client tells them that the server is active, but they cannot connect to it.

How do I fix that?

---

### Post by Lyerae on 2009-09-11
Bump.

---

### Post by mharrison on 2009-09-11
> **Lyerae said:**
> Hi, I'm trying to get the Ventrilo server to run on Linux. I can connect using "127.0.0.1", but people cannot connect using my IP.
The client tells them that the server is active, but they cannot connect to it.

How do I fix that?

Are you behind a router/firewall....are people trying to connect via the Internet or an internal LAN?  If you are trying to have people connect over the Internet and you are behind a router/firewall, you may have to setup rules to allow the connections to pass through to your computer.  

Not sure on the specifics of a Vent server as I haven't set one up, but if it's anything like trying to host a network game over the net, you will need to open some ports and such....but you have to explore the security risks of doing so.

---

### Post by Lyerae on 2009-09-11
I know the risks of opening ports... Allowing data to get through an unprotected hole in your computers security... etc.
They're trying to connect over the internet. I have no idea if it works on LAN. It does work on LocalHost though.

I'd have tried to open the ports, but I'm still new to Ubuntu (I've had it less than a week), and I have no idea how to do that.
The specific version I'm trying to install and run is "3.0.3", which has a specific Linux version, which is what I'm running. No Wine involved.

I am behind a router, but there are several ports already opened on the router (I opened them myself), so if possible, I'd like to be able to use those ports (6112-6118).

---

