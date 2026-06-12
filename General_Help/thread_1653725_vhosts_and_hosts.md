---
title: "vhosts and hosts"
date: 2010-12-27
forum: General Help
---

### Post by christophweise on 2010-12-27
Hi everybody,

I have some questions about virtual hosts and the hosts file. Currently I have a Mac OS X 10.6 running and installed Ubuntu Server on a virtual machine via vmware. Everything worked fine. After that I installed Zend Server on my Ubuntu Server which was also no problem. Now, if I type the server's ip-adress n my browser I can see my web project. everythings great.

Ifconfig tells me:

eth0      Link encap:Ethernet  HWaddr 00:0c:29:e9:4b:d7  
          inet addr:172.16.28.143  Bcast:172.16.28.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee9:4bd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:800763 (800.7 KB)  TX bytes:873190 (873.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17084 (17.0 KB)  TX bytes:17084 (17.0 KB)

Now I want to access different projects from different domains. How can I do that? I already added a project specific file inside the sites-available directory and linked it inside the sites-enabled directory. I just have a problem to manage the server names.

Can you help me? Thank you in advance.

BR,
Christoph

---

