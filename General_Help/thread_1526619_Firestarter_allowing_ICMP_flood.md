---
title: "Firestarter allowing ICMP flood"
date: 2010-07-08
forum: General Help
---

### Post by morhaven on 2010-07-08
Hi, I am using ubuntu 9.10 karmic with zabbix to Ping multiple sites I have. but the problem I am facing is that Firestarter 1.0.3  is blocking by default the ICMP echo replies for all these sites as they come back looking like a flood.

I have about 100 devices that I Ping every 5 sec.. 

How to I stop Firestarter from blocking the Flood, or allow it?

---

### Post by kanikilu on 2010-07-08
Do you have ICMP filtering turned off in the preferences?

Also, from the Firestarter docs:

> By default Firestarter allows ICMP traffic, although it throttles it somewhat to prevent excessive flooding or Denial of Service attacks.

I don't see anything in the manual or in the text configuration file in /etc/firestarter/ that indicates an easy way to disable this default throttling.

However, I know that Firestarter is just a front end to iptables, of which I'm not an expert, but I do know that iptables has rate-limiting:

[http://penguinsecurity.net/wiki/index.php?title=The_iptables_Rate-Limiting_Module#Incoming_traffic](http://penguinsecurity.net/wiki/index.php?title=The_iptables_Rate-Limiting_Module#Incoming_traffic)

And I skimmed through the following file:

/etc/firestarter/firewall

And noticed this section:

```
# --------( Rules Configuration - ICMP )--------
```

and if ICMP filtering is turned off, it uses the following rule

```
# Allow all ICMP traffic when filtering disabled
$IPT -A INPUT -p icmp -m limit --limit 10/s -j ACCEPT
$IPT -A FORWARD -p icmp -m limit --limit 10/s -j ACCEPT
```

To be perfectly honest, I'm not 100% sure, but I would think that simply increasing the 10 per second ("10/s") number to something higher might work. Obviously make a back up of this file before changing anything.

---

