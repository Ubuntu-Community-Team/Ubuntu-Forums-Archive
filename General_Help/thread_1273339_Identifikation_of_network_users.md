---
title: "Identifikation of network users?"
date: 2009-09-23
forum: General Help
---

### Post by Styx on 2009-09-23
Hi to all
I have a problem is seek to solve. I have to look over a network that is used to serve three appartements. The network has to stay wirreless. 
But since we owne the network we are responsible for the downloads that are done with it.

The question is:
How can i ashure that people are not able to download illigal data? OR
Is it possible to backtrace the packages to the person that downloaded them?
(within my network - so i can pass all claims to the person resonsible)

I have setup a ubuntu-server i like to integrate it in to the network i would appreschiate any idears or tips you can give me.
Thank: Leon

---

### Post by StuartN on 2009-09-23
> **Styx said:**
> How can i ashure that people are not able to download illigal data?

You can control who logs in to many routers by setting up a list of permitted MAC addresses. Controlling what they access once logged in is much harder (unless you wish to dedicate a PC as a proxy server). The router setup page is somewhere like 192.168.1.1, and should be password protected.

---

### Post by Styx on 2009-09-25
Thanks for the answer 

The problem is that i do know how to use a router and that i can control the access to the network that way. The network is setup with a WPA key anyway. 

What i am looking for is a way to restrict the access to different protocols such as P2P file sharing. The user have to be able to use the Internet but not to a full extend.
If somehow one is able to perform some illegal actions i want to be able to backtrack it. That way i have more chance that this illegal action dose not go to our account.

The plan at the moment is to set up a region server an use WPA-enterprise in combination with a firewall. A server will have to do that job. 

Any information about this is desperate needed.

---

### Post by StuartN on 2009-09-25
> **Styx said:**
> The problem is that i do know how to use a router

Just google for pdf documents with the model number and you are bound to find the manual. Some models of router will do everything you need to control access by user, time and service. Mine has a nice web interface that can deny P2P, or any other service, for all or individual users.

If you want to set up a fully traceable proxy, then have a look at squid [http://www.squid-cache.org/](http://www.squid-cache.org/)

---

### Post by Styx on 2009-10-12
Thanks 

That might help me out.

---

