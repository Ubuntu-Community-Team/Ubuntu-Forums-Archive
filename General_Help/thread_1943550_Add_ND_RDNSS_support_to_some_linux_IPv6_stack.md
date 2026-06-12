---
title: "Add ND RDNSS support to some linux IPv6 stack"
date: 2012-03-19
forum: General Help
---

### Post by lilipop on 2012-03-19
hi, 
i would like to implemmnet RDNSS suport for an linux version, so can  somebody help to give me some advices about on how to do it? 
if nobody knows, then can you tall me at least some places, forums,  people, or books from where to learn or other things from where i could  begin to start to do it?

---

### Post by lilipop on 2012-03-19
at least somebody know how can i see how that is implemented in ubuntu, bsd, solaris, or other OS  ?

---

### Post by HiImTye on 2012-03-19
[http://manpages.ubuntu.com/manpages/hardy/man5/radvd.conf.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/radvd.conf.5.html)

---

### Post by lilipop on 2012-03-22
hi, thank you for the answer, it was really very helpfull.
i saw this project(the ND RDNSS) in an open source company and i found it very interesting, so i wanted to pick up it and make it .
i have read the following link:
[http://tools.ietf.org/html/rfc6106](http://tools.ietf.org/html/rfc6106)

which describes the request for comments, but i have not understood yet its purpose,

for example, there is a paragraph that says the following:
    Neighbor Discovery (ND) for IP version 6 and IPv6 stateless address
    autoconfiguration provide ways to configure either fixed or mobile
    nodes with one or more IPv6 addresses, default routers, and some
    other parameters [RFC4861][RFC4862].

and my question is:  what kind of configuration can be done in a node with and also with more ip adresses?
   
  And there also is a reference to nomadic host, what is that? Why some hosts are nomadic?

---

### Post by lemming465 on 2012-03-23
> rfc6106 ... but i have not understood yet its purposeThe two things an IP network client most wants to know are:
(1) where is my upstream gateway router, so I can send packets off-link toward the general internet
(2) where is my DNS server, so I can translate host names into IP addresses

In IPv4-only networks, typically both of those are provided by DHCP.

Hardly anyone is running an IPv6-only network yet.  The classic answer for IPv6-only would have been to get the gateway from the router advertisement's sending address (link-local, fe80::/64 + the router's EUI-64 mapped ethernet host part) and the DNS server from DHCPv6.  Except, that large classes of clients (windows XP, Mac OS-X < 10.7) didn't implement DHCPv6.  And prior to 2012 most consumer-grade routers / broadband modems got DHCPv6 service *WRONG*.

The two responses to this were:
a) actual IPv6 deployments are mostly dual-stack IPv4 + IPv6 on the wire, with DHCPv4 for all network parameters except v6 gateway and v6 prefix, which come from the ICMPv6 router advertisements.  The hosts then autoconfigure their v6 host part ("SLAAC", stateless address autoconfiguration, RFC 4862).

b) adding new router advertisement options for specifying DNS servers and DNS default search suffixes.  RDNSS is not yet widely implemented, so expect (a) to continue for some years.

> ... what kind of configuration can be done in a node... 

Other things one might want to know about the local network include NTP time servers, legacy SYSLOG servers, legacy WINS servers, remote network boot servers, etc.  These are almost always going to come from DHCP, either v4 or v6.

> ...more ip adresses...
v4 assigned IP addresses to hosts, usually just one, and expected a typical host to have one network interface.  v6 assigns IP addresses to interfaces, anticipates that hosts might have multiple interfaces, and always uses multiple addresses on each interface.  In particular, a v6 host will be using both link-scope unicast addresses (fe80::/64 prefix) and global-scope unicast addresses (2000::/3) simultaneously.  Plus it will be using link-scope multicast addresses (ff02:: ) for router solicitation and neighbor discovery.

In v6, neighbor discovery replaces the v4 ARP protocol; both translate IP addresses into ethernet addresses by querying multiple hosts in parallel on the local link.  v4 ARP uses ethernet broadcast; v6 ND uses ethernet multicast.

> Why some hosts are nomadic?
A nomadic host would be one using the v6 mobility features to maintain persistent connections with services via a fixed home-agent address in spite of the fact that it's changing its live address and gateway as it moves between different network segments.  See RFC 6275, and ICMPv6 message types 144-147 (home agent request/reply, mobile prefix solicit/advertise).

---

