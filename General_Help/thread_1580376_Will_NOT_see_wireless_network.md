---
title: "Will NOT see wireless network"
date: 2010-09-23
forum: General Help
---

### Post by i-like-knives on 2010-09-23
When I first got this laptop,,I opened it up and it magically found my wireless network no prob. Well, I had probs with that modem (duz'nt it figure? after everything was wroking so well) and Verizon switched out to newER model,,same exact model, same number etc. Checked in the westell site (192.168.1.1) and the computer sees the wireless (and all) but will not connect to it. The modem sees all local wi-fis in this area. Yes,,I have been looking at google, etc and here for over a day now, with ](*,). Modem and Westell Mfr's site both show wireless network green light and both my wired(s) work just fine. Thanks,,,you folks always come through for me. I'm 47 and computer literate (given my lack of growing up with them),,just not a dba or code monster or anything,,just now learning the terminal, and can use it,,but know not the commands. Not a TOTAL beginner,,but not intermediate or advanced by any means.

Thanks again, and, Take care-Glenn:KS

---

### Post by TBABill on 2010-09-23
Trying to better understand your problem. You said you connected to the Westell and I assume you mean the type that is combination DSL modem and wireless router? And you said "the computer sees the wireless and all"....do you mean that you were on the wireless computer and typed  192.168.1.1 from that computer and got to the login page for the router? If so, you are already connected to that router. If you had to plug into the router to "see" it then the problem is different and you have not yet connected wireless-ly to it. 
 
If I'm not mistaken, with those Westells you have to actually "enable" the wireless side of them. I'm going from memory from when I was a VZ tech back in 2004, but I recall the wireless side of the modem/router having to be enabled. When you got in via 192.168.1.1, did you go to the wireless settings to make sure everything obvious was checked/enabled? If you are seeing all the other wifi enabled routers nearby then your computer is clearly working fine. 
 
If you can clarify a bit more exactly what works and what you have tried but did not work, more help will come your way. This shouldn't be too difficult unless the router has a physical problem.

---

### Post by termin on 2010-09-23
its most likely a hardware problem, because if your network card can sense it then it should connect to it automatically. 
run:
sudo ifconfig 
and then display the results.

---

### Post by i-like-knives on 2010-09-23
Rsults of <sudo ifconfig>

eth0      Link encap:Ethernet  HWaddr 00:23:5a:4b:3b:d9  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe4b:3bd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:328758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:145301739 (145.3 MB)  TX bytes:59396235 (59.3 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11752 (11.7 KB)  TX bytes:11752 (11.7 KB)

ra0       Link encap:Ethernet  HWaddr 00:24:2b:85:0f:a4  
          inet6 addr: fe80::224:2bff:fe85:fa4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:65531 errors:203 dropped:0 overruns:0 frame:0
          TX packets:75962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6132909 (6.1 MB)  TX bytes:6768 (6.7 KB)
          Interrupt:17 


Does this help?? Thanks

---

### Post by TBABill on 2010-09-23
Please post the model number of your Westel DSL modem/router. I do not know who your provider is so I looked up on Verizon's support site. Per the Westel 7500 guide,  > If you are connecting to VersaLink via a wireless network adapter, the SSID must be the same for both VersaLink and your PC's wireless network adapter. The default SSID for VersaLink is the SERIAL NUMBER of the unit (located below the bar code on the bottom of the modem and also on the shipping carton). You MUST connect to it first using its default SSID and then you can change it via the configuration procedures (according to their documentation). [http://onlinehelp.verizon.net/consumer/bin/pdf/VersaLink7500UserGuide.pdf](http://onlinehelp.verizon.net/consumer/bin/pdf/VersaLink7500UserGuide.pdf)
 
If you have another provider, model of unit, etc., just search for similar documentation to help you out.

---

