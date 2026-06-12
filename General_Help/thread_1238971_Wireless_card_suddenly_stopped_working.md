---
title: "Wireless card suddenly stopped working"
date: 2009-08-13
forum: General Help
---

### Post by colinireland on 2009-08-13
Hey,

Wondering if anybody can help. My wireless card has just stopped working. 

ifconfig eth1 gives:
eth1      Link encap:Ethernet  HWaddr 00:24:2c:71:a0:55  
          inet6 addr: fe80::224:2cff:fe71:a055/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000

iwconfig eth1 gives:
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

but when I go to select a wireless network using the icon near the clock I can't see any. Only when I plugged in my old external wireless card did I see my home network.

Does anybody know what is going on hear?
Thanks, Colin

---

### Post by Yvan300 on 2009-08-13
Try reinstalling the driver, this fixed my problem which is similar to yours.

---

### Post by colinireland on 2009-08-13
I have tried to reinstall the drivers as per [this post]("http://ubuntuforums.org/showthread.php?t=896713") but still no luck. I mean it worked fine when I installed ubuntu first. Today I did a fresh install and its not happening for me. Have you any other ideas as to what could be the problem?

---

### Post by Yvan300 on 2009-08-13
You could try anther version of ubuntu and hope that your driver works there, and also check to see if there are other wireless drivers offered for your card.

---

