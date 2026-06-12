---
title: "SSH/Network hostnames"
date: 2012-05-09
forum: General Help
---

### Post by Henkdroid on 2012-05-09
When using SSH with my old router I could type the command as "ssh user@hostname". My old router was a BT HomeHub 2, now I have switched ISP and have a TalkTalk router, which is a rebranded Huawei HG532, and now I have to use the command as "user@192.168.1.x". Has anyone else had this problem and knows how to fix it?

---

### Post by papibe on 2012-05-09
Hi Henkdroid.

It looks like your previous router also served as a Domain Name Server (DNS), thus helping you to translate the local machine names into IP addresses.

The new one seems to be unable to do that work, or it is not configured properly yet.

To confirm this, could you post the result of this commands from your machine?
```
ifconfig

nslookup ubuntu.com

dig ubuntu.com

route -n
```
Regards.

---

### Post by Henkdroid on 2012-05-09
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:7c:e9:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2950879 (2.9 MB)  TX bytes:2950879 (2.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:b8:24:ca  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:feb8:24ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1308943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:773847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1755219496 (1.7 GB)  TX bytes:84989120 (84.9 MB)

```

nslookup ubuntu.com
```
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156

```

dig ubuntu.com
```
; <<>> DiG 9.8.1-P1 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43833
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
ubuntu.com.		475	IN	A	91.189.94.156

;; AUTHORITY SECTION:
ubuntu.com.		45888	IN	NS	ns2.canonical.com.
ubuntu.com.		45888	IN	NS	ns3.canonical.com.
ubuntu.com.		45888	IN	NS	ns1.canonical.com.

;; Query time: 73 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed May  9 22:27:06 2012
;; MSG SIZE  rcvd: 108

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```
Thanks for your speedy reply.

---

### Post by papibe on 2012-05-09
Thanks.

I forgot 12.04 has a different DNS configuration. I'm going to have to get back to you in a few minutes.

In the meantime, if both machines are running Ubuntu, you may use this syntax to ssh:
```
ssh user@hostname**.local**
```
Regards.

UPDATE: It looks like your router does not work as a DNS (read about it [here]("http://talktalkmembers.net/forums/showthread.php?t=68975")).

---

### Post by papibe on 2012-05-18
Hi.

The definitive proof is in this command:
```
 cat /var/run/nm-dns-dnsmasq.conf
```
In my case, the router works as a local DNS for my network. This is my output:
```
server=192.168.1.254
```
That's is the LAN address of my router. If that file points to an address outside your LAN addresess range, it means that your router does not support DNS.

Did you try using the .local domain between Ubuntu machines?

Regards.

---

