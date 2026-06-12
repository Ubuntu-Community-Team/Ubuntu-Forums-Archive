---
title: "Ethernet not working"
date: 2011-02-20
forum: General Help
---

### Post by Rey117 on 2011-02-20
Hey guys its been awhile i haven't been on the forums but I seem to have run into some trouble with my Ethernet. I connect my ethernet cable into my laptop and it seem like a no go. I'm running Ubuntu 10.04 LTS. Thanks in advance!

---

### Post by cprofitt on 2011-02-20
lets figure out is your card is being detected.

run the following:

```

:~$ lspci | grep Ethernet

```

you should get a result that looks like this:

```

:~$ lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)

```

Assuming you get a device you can then do the following:

```

:~$ ifconfig

```

You should get out put that looks like this:

```

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr <redacted>  
          inet addr:192.168.1.196  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: <redacted> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71025843 (71.0 MB)  TX bytes:54770408 (54.7 MB)
          Interrupt:20 Memory:fc000000-fc020000 

```

If you are getting those things then it should be working... but there may be other issues such as DNS. If you do not get those please post your results.

---

### Post by Rey117 on 2011-03-06
```
eth0      Link encap:Ethernet  HWaddr 00:1e:33:69:1c:ad  
          inet6 addr: fe80::21e:33ff:fe69:1cad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32727 (32.7 KB)  TX bytes:2818 (2.8 KB)
          Interrupt:27 Base address:0xe000 

```
Sorry for the late response but I didn't have Internet for a week. This is the result I recieved.

---

### Post by cprofitt on 2011-03-06
You are not getting an IPv4 address, and the IPv6 seems to be auto-generated. What are you using as a DHCP server?

---

