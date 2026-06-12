---
title: "Wired connection not working 11.04"
date: 2011-10-04
forum: General Help
---

### Post by bfrederi on 2011-10-04
I'm unable to connect via my wired connection. I've verified that it's not the wiring or modem creating the issue. I have no problems connecting via wireless either.

When I run ifconfig, only lo and wlan0 show up. The typical eth0 is not there at all. I'm not sure what my wireless card is, but the laptop is a Dell Inspiron 1720. It only started doing this in a recent update of 11.04 as far as I know.

I'm not really sure what other information to provide for now, but I will provide whatever information I can if someone can help me out. Thanks.

---

### Post by varunsaini on 2011-10-05
Even I am facing same problem.

---

### Post by varunsaini on 2011-10-05
This is the response that I am getting for ifconfig-
varun@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:b8:79:9b  
          inet6 addr: fe80::a6ba:dbff:feb8:799b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:746 (746.0 B)  TX bytes:5599 (5.5 KB)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:6e:eb:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

