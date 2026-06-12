---
title: "choppy internet speeds"
date: 2011-08-18
forum: General Help
---

### Post by dummyvin on 2011-08-18
I'n new to Linux, and pretty new to scripting.
 
I'm experiencing very choppy internet speeds when using Ubuntu, using speedtest.net under windows 7 i have a solid download speed of around 21mbs, in ubuntu it'll rise to 4mb then drop harsly and keep riseing and falling non stop. And that's how it is when I surf the web, somethings will load quickly and then all of a sudden it just stops loading, load the page, then stop. 
 
I have my pc connected to my router by eathernet cable, and I have a Realtek 10/100/1000 RTL8111e chip on my motherboard. I tried updateing driver's but can't seem to figure it out.

---

### Post by papibe on 2011-08-18
Could you post the result of these commands?
```
$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

---

### Post by allwimb on 2011-08-18
could you also put the result of sudo iptables -L

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by dummyvin on 2011-08-18
I ran the code twice, once when my Internet connection was working good then again like 20secs later when it bogged down. 

Good Connection
```
aarvin@Azuura:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d9:2f:5f  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed9:2f5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405 errors:0 dropped:405 overruns:0 frame:405
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:408860 (408.8 KB)  TX bytes:74198 (74.1 KB)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

aarvin@Azuura:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
aarvin@Azuura:~$ nslookup ubuntu.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156

aarvin@Azuura:~$ dig ubuntu.com

; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53128
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.            IN    A

;; ANSWER SECTION:
ubuntu.com.        9    IN    A    91.189.94.156

;; Query time: 1 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Thu Aug 18 13:05:43 2011
;; MSG SIZE  rcvd: 44
```Bad Connection
```
aarvin@Azuura:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d9:2f:5f  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed9:2f5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5248 errors:0 dropped:5248 overruns:0 frame:5248
          TX packets:5563 errors:0 dropped:31 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5004702 (5.0 MB)  TX bytes:904336 (904.3 KB)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1548 (1.5 KB)  TX bytes:1548 (1.5 KB)

aarvin@Azuura:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
aarvin@Azuura:~$ nslookup ubuntu.com
nslookupubuntu.com

(right here it took a while to process, thought i typed it in wrong and tried it again when it didn't process immediately)

;; connection timed out; no servers could be reached


aarvin@Azuura:~$ dig ubuntu.com

; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

``````

aarvin@Azuura:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
aarvin@Azuura:~$ 

```

---

