---
title: "Open PORT newb question"
date: 2010-07-20
forum: General Help
---

### Post by MikeyDL on 2010-07-20
I been working on getting an ubuntu server up behind a firewall with openssh server.  I've opened a port (example:  222510) and in my sonicwall setting there the rules specify if you want to open a TCP or UDP port.  What is the difference?  I usually do a rule for each one but wondered if I only needed to bother with TCP?

---

### Post by bodhi.zazen on 2010-07-20
You only need tcp

[http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol)

[http://en.wikipedia.org/wiki/User_Datagram_Protocol](http://en.wikipedia.org/wiki/User_Datagram_Protocol)

Almost all of your servers will be tcp , so you can DROP or REJECT most udp traffic.

---

### Post by awi on 2010-07-20
> **MikeyDL said:**
> I been working on getting an ubuntu server up behind a firewall with openssh server.  I've opened a port (example:  222510) and in my sonicwall setting there the rules specify if you want to open a TCP or UDP port.  What is the difference?  I usually do a rule for each one but wondered if I only needed to bother with TCP?

It depends on the service. In your case, ssh is a tcp service, so you only need that one. 
It is very unusual a service that requires both (some DNS configurations use port 53 on both, tcp and udp, but for different purposes).
For most of the services you will need only one protocol.

---

