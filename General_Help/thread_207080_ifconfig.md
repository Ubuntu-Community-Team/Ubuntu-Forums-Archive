---
title: "ifconfig"
date: 2006-07-01
forum: General Help
---

### Post by lex1 on 2006-07-01
Doesthe line that startswith inet6 mean i am useing IPV6?

lex1




$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:5C:AF:1F  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe5c:af1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18946245 (18.0 MiB)  TX bytes:2035507 (1.9 MiB)
          Interrupt:201 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by xtacocorex on 2006-07-01
Yes, it means that ipv6 is enabled on your computer.

Most ISP's don't support it yet, so it is ok to disable it. By doing so, you will speed up your internet.

I don't remember the How-To thread, but I think someone posted it in another of your threads.

---

### Post by lex1 on 2006-07-01
look at last post in thread
[http://www.ubuntuforums.org/showthread.php?t=206723](http://www.ubuntuforums.org/showthread.php?t=206723)

---

