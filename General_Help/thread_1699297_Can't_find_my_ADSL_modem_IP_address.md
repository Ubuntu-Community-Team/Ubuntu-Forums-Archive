---
title: "Can't find my ADSL modem IP address"
date: 2011-03-03
forum: General Help
---

### Post by rva1945 on 2011-03-03
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8f:fb:59:84  
          inet6 addr: fe80::213:8fff:fefb:5984/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9468746 (9.4 MB)  TX bytes:19261716 (19.2 MB)
          Interrupt:22 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640 (640.0 B)  TX bytes:640 (640.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:190.49.191.206  P-t-P:200.51.241.231  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:47612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8371761 (8.3 MB)  TX bytes:18052094 (18.0 MB)

(190.49.191.206 is my dynamic IP it will change next time I connect to the Internet).

The modem is connected to the ethernet via RJ-45.

Thanks

---

### Post by blueridgedog on 2011-03-03
Your modem is not exposing it's IP to you, you would either need to see if it has a web server built in by going to the gateway IP it assigns you as a gateway with a web browser or going to an internet site that will tell you your ip.  You can see your gateway ip with the route command.

You can get your external ip at web sites such as:

[http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by rva1945 on 2011-03-03
Well, that's the IP that appears in the output, but  Unable to connect  BTW this is the ouput of the route command:  /$ route Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 200.51.241.231  *               255.255.255.255 UH    0      0        0 ppp0 default         *               0.0.0.0         U     0      0        0 ppp0  Then?

---

### Post by blueridgedog on 2011-03-04
In point to point mode, your router may not be getting an ip address.

[http://en.wikipedia.org/wiki/Point-to-Point_Protocol_over_Ethernet](http://en.wikipedia.org/wiki/Point-to-Point_Protocol_over_Ethernet)

Your interface is setup in pppoe mode:

inet addr:190.49.191.206 P-t-P:200.51.241.231

So, the 190 address is your end of the pipe and the 200 address is the other end of the pipe.  

What IP do you get when you check an IP identification website?

What are you trying to do that is failing?

---

