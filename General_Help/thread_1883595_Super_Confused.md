---
title: "Super Confused"
date: 2011-11-19
forum: General Help
---

### Post by hackerseraph on 2011-11-19
Hey guys, check this one out.

My 1 computer, running ubuntu 11.04 can not access apple.com all of a sudden. Other computers in the household can, that access my same router. The router is handing out dns via googledns. Ive tried it on 2 different browsers, [chrome and firefox] and mozilla thunderbird cant access the icloud mail servers.

When using a proxy, this computer can access apple.com

How is this even possible?

Let me know things I can reset that could possibly clear this up.

Networking issues are always fun, so I'm excited :D

:popcorn:

---

### Post by hackerseraph on 2011-11-19
changed my network ipv6 settings to link-local and suddenly it worked. o_O so confused right now

---

### Post by papibe on 2011-11-19
Hi hackerseraph.

Is is just apple.com? Can you access the other sites with no problem?

Could you also post the results of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig ubuntu.com

nslookup apple.com

dig apple.com
```
Regards.

---

### Post by hackerseraph on 2011-11-19
it seems its blocked again. as soon as i tried to add my @me.com email to thunderbird it stops the website, even from coming through to my virtual machines.

i just restarted my apple router. 

i checked gedit /etc/hosts to make sure it wasnt being blocked
---

```
marcus@marcus-Satellite-L505:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1e:65:52:6e:2e  
          inet addr:10.0.1.3  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe52:6e2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33597002 (33.5 MB)  TX bytes:4319097 (4.3 MB)


marcus@marcus-Satellite-L505:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 wlan0

marcus@marcus-Satellite-L505:~$ nslookup ubuntu.com
Server:		10.0.1.1
Address:	10.0.1.1#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156

marcus@marcus-Satellite-L505:~$ dig ubuntu.com

; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42766
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
ubuntu.com.		248	IN	A	91.189.94.156

;; Query time: 2 msec
;; SERVER: 10.0.1.1#53(10.0.1.1)
;; WHEN: Sat Nov 19 13:19:40 2011
;; MSG SIZE  rcvd: 44

marcus@marcus-Satellite-L505:~$ nslookup apple.com
Server:		10.0.1.1
Address:	10.0.1.1#53

Non-authoritative answer:
Name:	apple.com
Address: 17.149.160.49
Name:	apple.com
Address: 17.172.224.47

marcus@marcus-Satellite-L505:~$ dig apple.com

; <<>> DiG 9.7.3 <<>> apple.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23787
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;apple.com.			IN	A

;; ANSWER SECTION:
apple.com.		417	IN	A	17.149.160.49
apple.com.		417	IN	A	17.172.224.47

;; Query time: 2 msec
;; SERVER: 10.0.1.1#53(10.0.1.1)
;; WHEN: Sat Nov 19 13:21:02 2011
;; MSG SIZE  rcvd: 59


```

---

### Post by hackerseraph on 2011-11-19
and judging by those last outputs its working again

firefox >> apple.com >> pulled right up

so it seems on and off if im trying to add my @me.com [apple mobileme/ icloud] account into thunderbird it locks it up

the relation to the ipv6 was irrelevant, it just happened to be the timing.

lovin' this right now :D

edit: it seems to be coming and going. proxify lets me access it perfectly fine for now. im rather intrigued.

---

