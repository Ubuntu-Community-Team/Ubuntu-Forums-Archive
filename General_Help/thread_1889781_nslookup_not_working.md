---
title: "nslookup not working"
date: 2011-12-02
forum: General Help
---

### Post by baska on 2011-12-02
Hello brothers.

   This is my first thread to this forum. I'm new to linux world . If my thread is not related to this section, i request the moderator to move my thread .. 
On terminal i apply following command but nothing worked ..

baska@ubuntu:~$ ping [www.google.com]("http://www.google.com")
ping: unknown host [www.google.com]("http://www.google.com")
baska@ubuntu:~$ nslookup [www.google.com]("http://www.google.com")
;; connection timed out; no servers could be reached

baska@ubuntu:~$ dig [www.google.com]("http://www.google.com")

; <<>> DiG 9.7.3 <<>> [www.google.com]("http://www.google.com")
;; global options: +cmd
;; connection timed out; no servers could be reached
baska@ubuntu:~$ ping 192.168.21.200
PING 192.168.21.200 (192.168.21.200) 56(84) bytes of data.
64 bytes from 192.168.21.200: icmp_req=1 ttl=64 time=0.546 ms
64 bytes from 192.168.21.200: icmp_req=2 ttl=64 time=0.197 ms
64 bytes from 192.168.21.200: icmp_req=3 ttl=64 time=0.199 ms
64 bytes from 192.168.21.200: icmp_req=4 ttl=64 time=0.209 ms
64 bytes from 192.168.21.200: icmp_req=5 ttl=64 time=0.204 ms
64 bytes from 192.168.21.200: icmp_req=6 ttl=64 time=0.250 ms
64 bytes from 192.168.21.200: icmp_req=7 ttl=64 time=0.215 ms
64 bytes from 192.168.21.200: icmp_req=8 ttl=64 time=0.208 ms


I can ping to my local server but i can't ping outside my server .. nslookup is not working and dig also not working ..

This is my network configuration .. I'm using proxy 
IP Address 192.168.21.45
Subnet mask: 255.255.255.0
default route : 192.168.21.200
Dns : 192.168.100.13

thanks

---

### Post by JamieSK on 2011-12-02
Are you able to reach the DNS server? You may not be able to ping google.com because the name cannot be resolved. 
 
Are you able to reach any address outside your network?

---

