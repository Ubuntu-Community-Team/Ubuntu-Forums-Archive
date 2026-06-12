---
title: "networking problems, can ping sites but can't view them."
date: 2006-05-05
forum: General Help
---

### Post by thomas.mcmahon on 2006-05-05
Hey guys,

I'm having a networking problem that I don't understand. My router is connected to the net, and I can ping web servers like google etc. but if I try and open the sites with Firefox or Epiphany they don't work. However I can browse the web with Konqueror and Links.

I can't use irc or apt either, they keep saying that the address that I'm trying to access is 1.0.0.0 I'm not sure what that IP means. Anyone know what might be the problem?

Tom

---

### Post by dermotti on 2006-05-05
type ifconfig and paste your results in here

---

### Post by thomas.mcmahon on 2006-05-05
[QUOTE=dermotti]type ifconfig and paste your results in here[/QUOTE]

johnnybezak@atticus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:27:98:10:44
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20a:27ff:fe98:1044/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10748 errors:1 dropped:0 overruns:0 frame:0
          TX packets:10770 errors:3 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000
          RX bytes:4566869 (4.3 MiB)  TX bytes:1012215 (988.4 KiB)
          Interrupt:53 Base address:0x9400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1266731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1266731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:245565814 (234.1 MiB)  TX bytes:245565814 (234.1 MiB)

---

### Post by mikesull on 2006-05-22
I've had the same problem. From what I've gathered its a dns problem when using a router or modem/router. Even if ipv6 is disabled in firefox and from the entire system it doesn't help. I've found this bug in Fedora 4 as well. IF YOU DON'T USE A ROUTER THIS WILL PROBABLY NOT APPLY TO YOU!
You will be able to tell this is an dns issue by being able to ping any numerical IP address, but not a alphabetical address like "www.yahoo.com". Although even if you can ping some alpahbetical adresses it wouldn't hurt to try.
I have an Actiontec DSL gateway modem/router, and after trying over a dozen different things in different ordrers I found and easy fix. 
Log into your router through a web browser, mine is 192.168.0.1. Find what your dns server IP's are (on my router there under "status"). Copy these 2 adresses down. Then go to System->Administration->Networking, or network-admin in the comand line. Click on the DNS tab and enter the DNS server addresses you got from your router are on the top of the list.

---

