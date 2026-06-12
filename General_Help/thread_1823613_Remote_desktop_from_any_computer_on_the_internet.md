---
title: "Remote desktop from any computer on the internet"
date: 2011-08-12
forum: General Help
---

### Post by Nathan_M on 2011-08-12
I'd like to set up remote desktop which I can access from any computer with a VNC client, without knowing the IP address in advance and without having access to the "server" at the time of access. I'm aware of the security risks, but there's nothing critical on the server computer, and I'll make sure I use a good password, so I'd still like to go ahead. Is this possible?

---

### Post by aeiah on 2011-08-12
yea its possible. set up a vnc server on your machine, forward the required ports on the router, and use dyndns so you have a consistent and memorable server name for the outside world

---

### Post by Nathan_M on 2011-08-12
Yeah, that makes sense. Everything I Google'd made it much more complicated than that, but that was probably because they went for the higher security openssh option. I'll give it a go when I get back to my machine this evening.

---

### Post by Nathan_M on 2011-08-12
Hmmm... can't seem to make it work.

It works on the local network, connecting through 192.168.0.5:5900. I've set the following rule under "Inbound services" on the router:

Service: VNC(TCP:5900-5900)
Action: ALLOW always
Send to LAN server: 192.168.0.5
WAN users: ANY

I'm not sure what the last part is supposed to do... I can set a different IP for the WAN, but following instructions online for my model of router suggests leaving it to ANY. Seems counter-intuitive to me, but it won't let me leave the LAN server blank, so not sure what else I can do. Tried putting the same IP in again in WAN users but it didn't make any difference.

Sorry, this isn't so much an Ubuntu question anymore as a router question, but figured someone might know.

---

### Post by papibe on 2011-08-12
There are several things you need to do to make it work, and that implies understanding several concepts like static vs. dynamic IP addreses, DNS, etc.

This is a [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.

---

### Post by Nathan_M on 2011-08-12
I get that, but surely until I get that sorted out I can just use the IP address as-is. i.e. 90.208.xxx.xxx:5900? I know that IP address is still the same for now because I just checked.

---

### Post by spiky001 on 2011-08-12
So can you explain what you have tried so far. Have you set the firewall to allow connections from the internet

---

### Post by papibe on 2011-08-12
In order to test the access to your server from the Internet, you have to really try it from outside. For example an Internet cafe, public library or better a friend's house. Another alternative is to use your phone with the 3G service (not WiFi).

What happens is it is very difficult to find these days a modem that supports 'NAT loopback', i.e., the ability to connect to your local server from your LAN using its public IP.

Regards.

---

### Post by Nathan_M on 2011-08-12
> **papibe said:**
> In order to test the access to your server from the Internet, you have to really try it from outside. For example an Internet cafe, public library or better a friend's house. Another alternative is to use your phone with the 3G service (not WiFi).

What happens is it is very difficult to find these days a modem that supports 'NAT loopback', i.e., the ability to connect to your local server from your LAN using its public IP.

Regards.

Ah, that's where I was going wrong. It works beautifully from my phone. I tried that already, but I think I had some of the settings wrong when I tried it before. Thanks a lot.

---

