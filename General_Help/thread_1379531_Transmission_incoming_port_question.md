---
title: "Transmission incoming port question"
date: 2010-01-12
forum: General Help
---

### Post by baichi9992 on 2010-01-12
**Transmission incoming port question** 
Hi all,

I'm running v 1.06 of transmission and was having great DL speeds but now it seems to have really slowed. One thing I [noticed is that in]("http://aionlevelbot.net") preferences it tells me the incoming TCP port is closed (51413) but it's definitely open on my router to the right IP (static) and also canyouseeme.org shows it as open (I have a static IP on my cable modem as well). 

Why would transmission tell me it's closed and could that be the cause of some slowness? I think not since I was getting great speeds before and it might just be general traffic but I wanted to check.

thanks!

---

### Post by lovinglinux on 2010-01-12
> **baichi9992 said:**
> [B]Why would transmission tell me it's closed and could that be the cause of some slowness? I

Because it probably relies on querying a server and checking if the server can connect back using the selected port. If the server is down or if there is some problem in the network path to the server, then Transmission thinks the port is closed. Don't worry, if canyouseeme.org says it is open, then it is.

Having a closed port will slow you down only if the swarm is not big enough, because connections will still be requested by your client, which doesn't required port forwarding. Only incoming unrequested connections will be lost. Nevertheless, once you connect to a peer, then all data transfer is allowed both ways, no matter if the port is closed on the router or not.

You need to check if you are connected to enough peers. If not, then you might have a tracker issue.

I explain these concepts better in the tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). Take a look at the troubleshooting section.

---

