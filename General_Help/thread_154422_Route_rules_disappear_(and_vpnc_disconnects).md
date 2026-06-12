---
title: "Route rules disappear (and vpnc disconnects)"
date: 2006-04-03
forum: General Help
---

### Post by relix on 2006-04-03
When I add the following route rule:
**sudo route add -net 172.16.71.0 gw 172.16.70.253 netmask 255.255.255.0 eth0;**
everything works great for some time. I can access the 172.16.71.0 network which means the route rule is correct.

After a random time however, >20min to a few hours, the rule I added to route disappears. The rules that are in there from start-up don't, it's just the one that I add manually that disappears.

A (probably unrelated problem) is that my vpnc disconnects after a random time as well, but not together with the route-rule that disappears. Vpnc stays running, and I just have to do
**sudo vpnc-disconnect; sleep 1; sudo vpnc;** to get it up again, but it's a real nuisance.

Any help towards identifying the problem would be greatly appreciated.

---

### Post by lreyes6 on 2006-04-03
why don't you try to add a static route to your start up?

read [this]("http://ubuntuforums.org/showthread.php?p=217263")

hope this help

---

