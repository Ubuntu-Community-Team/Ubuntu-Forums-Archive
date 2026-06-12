---
title: "How can I use ssh as a cheap VPN/Proxy server?"
date: 2011-08-19
forum: General Help
---

### Post by gunksta on 2011-08-19
I'm trying to make it easier for me to work from home.

Here's my situation. I have a laptop running Ubuntu (not the problem) and I want to connect to a FTP server. Filezilla works really well and so does good old ftp. But, the FTP server I need to connect to will only accept connections from a white-list of addresses. My office IP is static and is on the list. Thus, connecting to this FTP server from the office is a piece of cake. 

But, I want to connect to this FTP server from home. Connecting to it directly from home is impossible because I have a dynamic IP address here at the house (surprise) so we can't just add my home IP address to the list.

Fortunately, I have full admin rights on the network at my local office and I installed cygwin on the Windows 2008 server. I can successfully connect to it using ssh. That gets me half way there. I can securely connect to a machine that is allowed to talk to the FTP server. I'm half way there. Now I want to figure out how to forward my ftp port over ssh through the server at the office and to the FTP server that I really want to connect to.

I've tried various incantations of ssh and I can't seem to come up with the right combination. Anyone have any experience doing something like this? In affect, I want to use ssh as a simplistic proxy and it need only really handle a single port.

Not sure if this is even possible.

Thanks

---

### Post by ziekfiguur on 2011-08-19
An ssh tunnel should be able to do the trick, here is a simple tutorial: [http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

---

