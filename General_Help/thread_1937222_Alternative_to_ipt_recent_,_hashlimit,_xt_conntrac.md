---
title: "Alternative to ipt_recent , hashlimit, xt_conntrack"
date: 2012-03-07
forum: General Help
---

### Post by theoneone on 2012-03-07
As the title says, I'm looking for alternative for iptables module above. The main reason is, currently my box only supports these modules:

cat /proc/net/ip_tables_matches
> 
udp
tcp
owner
state
length
ttl
tcpmss
multiport
multiport
limit
tos
icmp


I'm looking a firewall rules to limit max concurrent connections per IP... Something like [DDOS Deflate](http://deflate.medialayer.com), but also works for other protocol like UDP and ICMP (DDOS deflate only supports TCP)...

Thanks for your attention :)

---

