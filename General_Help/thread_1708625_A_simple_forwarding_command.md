---
title: "A simple forwarding command?"
date: 2011-03-16
forum: General Help
---

### Post by nkae100 on 2011-03-16
> iptables -A FORWARD -p tcp -i INTERNET --dport 80 -d 192.168.56.101 -j ACCEPT

I've been given this command which allows me to forward incoming port 25 connections to 192.168.56.101. What I was wondering though is if its possible to specify a port for the destination IP address?

I want to forward connections from port 25 to 192.168.56.101 on port 2525

---

### Post by Old *ix Geek on 2011-03-16
```
man iptables
```

will tell you everything you ever wanted to know about iptables. :)

---

### Post by nkae100 on 2011-03-16
That command did not solve my issue.

---

### Post by Old *ix Geek on 2011-03-16
> **nkae100 said:**
> That command did not solve my issue.You read the man page for iptables but didn't find the info you needed in it? :confused:

---

### Post by nkae100 on 2011-03-16
Its a thousand page long. I have a life.

I am wanting to make traffic pass through my computer to another computer.


Here is my current relative network setup:

[WAN] > [MODEM] > [10.1.1.3] > [192.168.56.101]


How can I make my computer ([10.1.1.3]) forward incoming traffic on port 25 to [192.168.56.101]?

---

