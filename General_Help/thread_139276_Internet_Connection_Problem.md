---
title: "Internet Connection Problem"
date: 2006-03-03
forum: General Help
---

### Post by cubbuk on 2006-03-03
Hi, 
I am connecting to internet through cable connection, I am using also a router, I can connect to internet with Windows and Pardus(linux based OS), I start to use Ubuntu 5.10, and I can ping my internet providers address(192.168.1.1) but can't connect to any other page, what should I do for repairing the connection? Thanks.

---

### Post by jamesr on 2006-03-03
> I can ping my internet providers address(192.168.1.1)

I do not believe that is your ISP's address that is a private network address. It is your router's address.

Post the output of 
```
sudo ifconfig -a
sudo iwconfig

```

---

### Post by cubbuk on 2006-03-04
You are right it is my router's address sorry about that

Output of ifconfig -a
eth0          Link encap: Ethernet HWaddr 00:0C:6E:86:16:8E
                inet addr:192.168.1.4      Bcast:192.168.1.255 Mask:255.255.255.0
                inet6addr: fe80::20c:6eff:fe86:168e/64 Scope:Link
                UP BROADCAST RUNNING MULTICAST MTU 1500 Metric:1
                RX Packets: 13 errors:0 dropped:0 overru&#305;ns:0 frame:0
                TX packets: 25 errors:0 dropped:0 overruns:0 carrier:0
               collisions: 0 txqueuelen:1000
                RX bytes:2425 (2.3 KiB) TX bytes:3422 (3.3 KiB)
                Interrupt:18 Base address: 0xd000
iwconfig's output
lo no wireless extension
eth0 no wireless extension
sit0 no wireless extension

---

### Post by cubbuk on 2006-03-04
Please heeeelp = (

---

### Post by jamesr on 2006-03-04
Try 
```
ping www.google.com
```

Post the output 

```
cat /etc/network/resolv.conf
```

---

### Post by cubbuk on 2006-03-05
ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

etc/resolv.conf
search company.com
nameserver 192.168.1.1

there isn't  etc/network/resolv.conf
I think nameserver should be different, what should I do?

---

### Post by Death on 2006-03-05
I am getting the same errors. Any help would be appreciated.

---

### Post by cubbuk on 2006-03-05
Please can someone help? I think name server should be different than 192.168.1.1, what should I do? Thanks

---

### Post by jamesr on 2006-03-05
Sorry about saying /etc/network/resolv.conf, it is, as you found /etc/resolv.conf

Yes Your current name server is the the router and that will not work.
The name server is the address given to you by ISP and is often found on their home page. The search is normally also provided by the ISP, but apparently is not always provided so you may have to comment out the search line as well.

**search **
this keyword specifies a list of alternate domain names to search for a hostname 
**nameserver **
this keyword, which may be used many times, specifies an IP address of a domain name server to query when resolving names

---

### Post by cubbuk on 2006-03-06
well it looks like when I edit the resolv file and change the nameserver it works, I hope it doesn't broke again when I restart. Thanks for help

---

### Post by Zalbor on 2006-03-06
I have a dsl connection, and I've set ubuntu's DNS server as my router's IP. It works fine...

---

