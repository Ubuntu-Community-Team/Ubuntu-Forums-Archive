---
title: "No avahi-daemon on server Lucid"
date: 2010-06-06
forum: General Help
---

### Post by papibe on 2010-06-06
After upgrading from scratch to Ubuntu server 10.04 (previously 9.10), I noticed that my server was cast out of the Cheers bar  :confused:, i.e., nobody knows its name anymore! (I have several Linux boxes on my home network).

Is there a new direction on how local networks are supposed to be configured? a new protocol?

I know my problem is solved by simply installing avahi-daemon, but I wonder how other people are dealing with this issue.

Thanks in advance,
Regards.

---

### Post by Iowan on 2010-06-06
I've never had much luck with **avahi** - but I haven't built a Lucid server, either... My "new" server is Hardy.  

Configuration via */etc/network/interfaces* doesn't work?

---

### Post by papibe on 2010-06-06
Let me give you more information: my server boots well, get his IP using dhcp (via the modem/router), and in general works fine (I'm even running transmission-daemon).

My problem is that from the server, ping only resolves my wife's Vista desktop (because samba is installed). Any other name outside the windows domain does not get resolved (2 other Linux machines).

When the server was running Jaunty, I had no problem because all linux names got resolve using the "host.local" format (avahi).

I think that my problem lies on the fact that I supersede the DNS on dhclient.conf, so that I can use OpenDNS (my ISP's DNS sucks big time). So it seems the server is not asking the router for local names.

Is there a any way to both skip my ISP's DNS and use the router for local names? 

Regards.

---

### Post by BoneKracker on 2010-06-06
Does the router actually have a dns server on it?  Most commercial routers don't.  Those that support open firmware often have dnsmasq, which can function as a dhcp and dns server integrated together.  This is a good way to provide name resolution for a small network.  If it does, ignore the rest of this post (the problem then is configuring that correctly).

Unless you are using IPv6 or otherwise have externally-visible IP addresses for each machine on your network (i.e., you are not using NAT), then an external DNS server is not going to provide name resolution for the addresses internal to your network.

Your options (based on my limited experience):

a) Put Avahi on the server.  Personally, I hate avahi and instinctively think of it as a security risk, but I think many people would disagree with that.

b) "Hard code" all your IP addresses into /etc/hosts and configure your router's dhcp server to always issue the same IP addresses to each machine (if it happens to have that capability)

c) Establish a dns server internal to your network and integrate it with your dhcp server for dynamic dns updates (the easiest way I know of to do that is dnsmasq (e.g. on your router or on your server), although I'm sure smarter people can do it with BIND and ISC DHCP).  If you put dnsmasq on your server, you'll want to turn of dhcp service of your router and use dnsmasq for both dhcp/dns instead.

---

### Post by papibe on 2010-06-07
I'll take a look into dnsmasq, thanks BoneKracker :).

---

### Post by BoneKracker on 2010-06-08
> **papibe said:**
> I'll take a look into dnsmasq, thanks BoneKracker :).

One odd thing about dnsmasq is the apparent lack of documentation.  The extensively-commented configuration file serves as its own documentation, although there is also a man page.

So, when you're researching it on the web, don't be intimidated by the fact that it doesn't have a glitzy web page with a wiki and all kinds of documentation.  It's pretty self-explanatory once you get it installed.  Just read the whole config file through once, then go back and change the things you want.

Let me know if you decide to try it and need any help.

---

