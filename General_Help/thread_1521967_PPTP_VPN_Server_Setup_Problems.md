---
title: "PPTP VPN Server Setup Problems"
date: 2010-07-01
forum: General Help
---

### Post by Metallinut on 2010-07-01
I've been at this for a while now. I'm trying to set up a VPN server on my Ubuntu machine. Ultimately the goal is to be able to connect my Droid smartphone to any wireless connection (or even the cell network) and have all my traffic routed through my home connection. Here are the particulars:

Ubuntu 10.04 on a virtualbox client (iMac OS X 10.6 host). I've got pptpd up and running, and I can actually connect via my phone over the cell network. It appears that I can route IP traffic, as I can plug in IP addresses in my browser (e.g. m.cnn.com -> 157.166.173.183) and I actually get the page. If I try using the fqdn though, I get nowhere.

So it would seem that VPN is working, all but for DNS queries. I cannot figure out how this may have gone wrong! Some of the tutorials I've been working with:

[Tutorial 1]("http://cviorel.easyblog.ro/2009/02/09/how-to-set-up-a-vpn-server-on-ubuntu/")
[Tutorial 2]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")

The Ubuntu virtualbox machine is set up for a bridged network connection, with its own IP address. Initially I thought this could be throwing a monkey wrench in everything, but if I use http to the IP address, it works. So it seems traffic is being forwarded correctly...except for DNS, which is kind of important.

I should add that my firewall on the router is configured for proper port forwarding (TCP 1723, IP 47 (GRE), UDP 500, UDP 4500), and I've run network traces to verify that the PPTP connection is being established.

Any ideas?

---

### Post by Metallinut on 2010-07-02
SOLVED!

If anyone else is having this problem...:

Turns out I needed to turn on some dns servers in /etc/ppp/options

```
ms-dns <dns.ip.add.ress>
ms-dns <2nddns.ip.add.ress>
```

It through me off, as the comments say it's for MS clients, and I'm using my Droid. But once I restarted pptpd everything works like a charm!

---

