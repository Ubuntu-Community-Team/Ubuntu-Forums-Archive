---
title: "How do I get Netstat to show DNS lookups?"
date: 2012-03-10
forum: General Help
---

### Post by chazinams on 2012-03-10
When using the Netstat command in the Terminal to see network connections as they occur, why doesn't it report DNS connections?

When Firefox connects to the internet and does a DNS lookup of a website I'm trying to connect to, how do I get Netstat to show this DNS lookup request to port 53 in the Terminal read out?

---

### Post by dcstar on 2012-03-10
> **chazinams said:**
> When using the Netstat command in the Terminal to see network connections as they occur, why doesn't it report DNS connections?

When Firefox connects to the internet and does a DNS lookup of a website I'm trying to connect to, how do I get Netstat to show this DNS lookup request to port 53 in the Terminal read out?

Because DNS lookups are UDP and not TCP, and these are stateless connections that don't hang around long enough to be seen in that way.

---

### Post by raja.genupula on 2012-03-10
+1  good article 
[http://beginlinux.com/blog/2009/01/dns-tools/](http://beginlinux.com/blog/2009/01/dns-tools/)

---

### Post by chazinams on 2012-03-11
> **dcstar said:**
> Because DNS lookups are UDP and not TCP, and these are stateless connections that don't hang around long enough to be seen in that way.

The application-firewall I use in M$ Windows can report and block UDP "stateless" DNS lookups. But Netstat can't even report when they occur? The stateless lookup request is leaving the Host computer, so why can't Netstat "see" this and report it?

---

### Post by dcstar on 2012-03-11
> **chazinams said:**
> The application-firewall I use in M$ Windows can report and block UDP "stateless" DNS lookups. But Netstat can't even report when they occur? The stateless lookup request is leaving the Host computer, so** why can't Netstat "see" this and report it?**

Because it is **different**. Find another tool to do it.

---

### Post by chazinams on 2012-03-11
Do you happen to know of a tool?

---

### Post by Doug S on 2012-03-11
You could use tcpdump (or wireshark, if you prefer) to observe DNS type packet traffic. Example```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth1 port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2012-03-11 19:04:03.275615 IP 209.121.28.192.46968 > 75.153.176.1.53: 13981+ [1au] A? bcferries.com. (42)
2012-03-11 19:04:03.324148 IP 75.153.176.1.53 > 209.121.28.192.46968: 13981 1/0/1 A 69.90.97.140 (58)
2012-03-11 19:06:05.337337 IP 209.121.28.192.30715 > 75.153.176.1.53: 5743+ [1au] A? a568.d.akamai.net. (46)
2012-03-11 19:06:05.384990 IP 75.153.176.1.53 > 209.121.28.192.30715: 5743 5/0/1 A 204.203.18.154, A 204.203.18.168, A 204.203.18.153, A 204.203.18.145, A 204.203.18.155 (126)

```

---

