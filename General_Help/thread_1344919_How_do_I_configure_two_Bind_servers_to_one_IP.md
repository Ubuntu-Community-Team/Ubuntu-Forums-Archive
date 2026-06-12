---
title: "How do I configure two Bind servers to one IP?"
date: 2009-12-03
forum: General Help
---

### Post by Modeverything on 2009-12-03
I hope this is the right forum post for this.  I couldn't really find a good place for this question.

I am trying to figure out a way to have two or more Bind servers mapped to the same IP address, so that if one goes offline, the other will continue to respond to requests sent to that same IP.

We primarily have a Microsoft shop here, and all of our client systems are Microsoft.  When a MS client boots, it finds a DNS server to use, and if that server goes offline, it won't failover to the secondary one, it just fails its look up.  Apparently with MS clients, the secondary DNS server setting will only help when it makes its choice when the network initializes.  Anyway, sometimes our MS DNS servers have to go offline for patching and other reasons, and when they do, all clients stop working until the server comes back.  I would like to setup two or more Bind servers with a shared IP address that all of my clients can point to, and if one of the Bind servers goes down, the other one can still respond to requests on that IP, so clients always continue to work.

Can anyone assist me with what I should use to do this?  I've tried to find ways to do it with clustering, Linux Virtual Server, and some other ideas that I've seen on Google, but none really seem to address the issue of two separate servers sharing the same IP.

Thanks in advance!

---

### Post by Modeverything on 2009-12-03
Figures after I post this, I think I found the answer.  I found the Linux High-Availability (Linux-HA) package.  Part of this includes a Heartbeat subsystem that, and I quote,



"It will run scripts at initialisation, and when machines go up or down. This version will also perform IP address takeover using gratuitous ARPs."

[http://packages.ubuntu.com/dapper/heartbeat](http://packages.ubuntu.com/dapper/heartbeat)

[https://wiki.ubuntu.com/UbuntuHighAvailabilityTeam/Heartbeat](https://wiki.ubuntu.com/UbuntuHighAvailabilityTeam/Heartbeat)



I think this is what I was looking for.  I'm going to do more research on it.

---

