---
title: "transmission broken ubuntu 12.04 TLS"
date: 2012-08-19
forum: General Help
---

### Post by spitfire1 on 2012-08-19
Brand new install.
ubuntu 12.04
opened a torrent with transmission and it fails to connect.
time unknown 0% and eventually stalls
error connection failed
network tab test port - port closed.

this all worked with previous versions of ubuntu

I am behind a firewall that uses PAT

I just installed deluge and have the same problem.

I know the network has not changed, so it leaves me to figure out what is different between the torrent clients on 12.04 and other versions of ubuntu that worked just fine.
p.s.
You do not have permission to create tags. You may only use existing tags.

where do you find existing tags

---

### Post by spitfire1 on 2012-08-19
Seriously thinking about not using Ubuntu 12.04

I created a static NAT mapping for my box - to no avail
I allowed specific incoming port in the firewall.

test if the port is open - this reports port closed

did a netstat - and can see the port is listening

So at this point if bitorrent is going to remain unusable I may roll back to an earlier version of ubuntu.

So I went to canyouseeme.com

and it reports that my IP and port can be seen.

locally I can telnet to the selected port

---

