---
title: "iptables to override shorewall"
date: 2011-11-13
forum: General Help
---

### Post by sparky-steve on 2011-11-13
Hello,

I'm running ubuntu server 10.04.3 LTS as a firewall/router. I'm using shorewall to set up the general connections, but have recently started using manual iptable commands to manipulate between shorewall restarts.

My default policy denies all outbound connections, and so all connections are explicitly allowed in shorewall/rules.

I also use squid as a transparent proxy on port 3128.

What I'm trying to achieve is a timer for the kids internet access; most of which I've successfully implimented.

For example, to turn off their "normal" internet access, I just run:

```
iptables -L lan2net --line-numbers |grep 192.168.1.101 |awk '{print "iptables -D lan2net "$1}'|csh && conntrack -D -s 192.168.1.101
```

which finds the rule in the lan2net section, deletes it, then deletes all current connections using conntrack. All new and existing (non www connections) are stopped.

BUT... that does not stop squid connections.... I thought the following would sort that:

```
iptables -L lan2fw --line-numbers |grep 192.168.1.101 |awk '{print "iptabled -D lan2fw "$1"}'|csh && conntrack -D -s 192.168.1.101
```

And it does indeed remove the redirect from the chain... but it still redirects to squid.....

I've looked at the output of "iptables -L" until my eyes hurt, and I cannot see how/why the connections are still being redirected to squid.....

If I simply remove (or comment out) the two rules in shorewall/rules that allow net access and squid redirection, it does work....

Any ideas?

Cheers
SS

NB: I know I'm mixing shorewall and iptables, and ideally this isnt good, and I am intending to move over to iptables and my own scripts completely in good time, but my network is diverse and complex (with lan2lan vpns, etc) and so for now, I need the reliability of shorewall until I fully understand iptables.

---

### Post by sparky-steve on 2011-11-14
Solved.

Should anyone from the future want to know, I found another table in iptables that handles redirections. this is the nat table.....

```
iptables -t nat -L lan_dnat --line-numbers |grep 192.168.1.101 |awk '{print "iptables -t nat -D lan_dnat "$1}'|csh && conntrack -D-s 192.168.1.101
```

That, in addition with the two previous commands does exactly what I need... Your mileage may vary.

---

