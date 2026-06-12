---
title: "Opening port issue"
date: 2010-05-09
forum: General Help
---

### Post by CommanderOne on 2010-05-09
Hey,

I'm trying to set up my newly installed Ubuntu laptop for torrenting, but I am having an issue. 

The speeds I have been getting quite honestly suck, nothing above 35 kb/s, which made me think of router issues. So I ran a few port checks, and they came up in 'stealth', so I port forwarded the router, ran the connection checks again and they came up 'closed', which makes me think the router is set up as it should be, and the problem is now with my laptop, or OS.

I've tried running a few Torrent Clients, and on advice settled with uTorrent through wine.

So basically, how do I open a port in Ubuntu 10 so I can torrent with decent speeds?

Thanks in advance.

---

### Post by 3rdalbum on 2010-05-09
You're getting a bit confused here. "Stealthed" means that it's hitting a firewall. "Closed" means that there's nothing listening on that selected port. So you don't need to "open" the port, just run a program that will listen.

Ubuntu 10.04 doesn't block any incoming connections, by default. It's just that nothing is listening.

Different Bittorrent clients use different ports, and some even use a different port each time you open them. Just make sure that your client is set to use the port that you have forwarded on your router, and that you've forwarded the port to the correct computer.

If in doubt, enable UPnP in the client and on the router to have the ports automatically forwarded.

---

