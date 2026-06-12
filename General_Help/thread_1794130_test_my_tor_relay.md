---
title: "test my tor relay"
date: 2011-06-30
forum: General Help
---

### Post by d3v1150m471c on 2011-06-30
Okay so I just started using a new isp and i'm trying to run a tor relay. Here's my setup:
```

Nickname d3v1150m471c
ORport 9001

``````

d3v11@d3v11m4ch1n3:~$ sudo nmap -sS 192.168.xx.xx -p 9001

Starting Nmap 5.00 ( http://nmap.org ) at 2011-06-30 14:13 EDT
Interesting ports on d3v11m4ch1n3 (192.168.xx.xx):
PORT     STATE SERVICE
9001/tcp open  tor-orport

Nmap done: 1 IP address (1 host up) scanned in 0.16 seconds
d3v11@d3v11m4ch1n3:~$ sudo nmap -sS xx.xx.xx.xx -p 9001

Starting Nmap 5.00 ( http://nmap.org ) at 2011-06-30 14:13 EDT
Interesting ports on xxxxxx (xx.xx.xx.xx):
PORT     STATE    SERVICE
9001/tcp filtered tor-orport

Nmap done: 1 IP address (1 host up) scanned in 1.59 seconds

```It looks like my relay is working, and I've setup port forwarding which you can see is working, but is there any other way to verify my relay is up? Like finding my nickname on the tor site, ect ect? Thanks in advance.

---

### Post by d3v1150m471c on 2011-06-30
Yay! using `cat /var/log/tor/log`:
```

Jun 30 14:48:28.729 [notice] Now checking whether ORPort xx.xx.xx.xx:9001 is reachable... (this may take up to 20 minutes -- look for log messages indicating success)
Jun 30 14:48:41.907 [notice] Self-testing indicates your ORPort is reachable from the outside. Excellent. Publishing server descriptor.

```

---

