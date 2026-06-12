---
title: "trying to link two pc using RJ45 cable"
date: 2010-07-07
forum: General Help
---

### Post by Spikerok on 2010-07-07
PC A - Ubuntu Desktop 9.10
[PHP]eth0      Link encap:Ethernet  HWaddr 00:16:d4:99:91:61  
          inet addr:169.254.0.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 
[/PHP]
PC B - Ubuntu Server 8.10
[PHP]eth0      Link encap:Ethernet  HWaddr 00:16:d4:99:91:61  
          inet addr:169.254.0.2  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 
[/PHP]

After connecting them with cable nothing happened. Light didn't flash.
How to fix it? Aim is to be able to access PC B using FTP and SSH.

---

### Post by jeebustrain on 2010-07-07
are you using a crossover cable?

---

### Post by bobcollard on 2010-07-07
> **Spikerok said:**
> PC A - Ubuntu Desktop 9.10
[PHP]eth0      Link encap:Ethernet  HWaddr 00:16:d4:99:91:61  
          inet addr:169.254.0.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 
[/PHP]PC B - Ubuntu Server 8.10
[PHP]eth0      Link encap:Ethernet  HWaddr 00:16:d4:99:91:61  
          inet addr:169.254.0.2  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 
[/PHP]After connecting them with cable nothing happened. Light didn't flash.
How to fix it? Aim is to be able to access PC B using FTP and SSH.
Are you using direct Ethernet wire or through a router?  Direct wire requires a crossover cable, see this link.
[http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp](http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp)

---

### Post by Spikerok on 2010-07-07
Yes, here is picture of it:

[IMG]http://www.harting.co.uk/imperia/md/images/lg/hartingconnectivitynetworks/products/deviceterminationdecivecon/hartingrjindustrialrj45/hartingrj-industrial_-rj45-700.jpg[/IMG]

---

### Post by Spikerok on 2010-07-07
Ahh i see, so they are actually differently connected...

---

### Post by Spikerok on 2010-07-07
Then im using Standard Ethernet Cable

---

### Post by bscbrit on 2010-07-07
Are you sure that you have shown us the correct information, because it doesn't look like a cut-and-paste?  Both computers have the same Hardware address - so I suspect that you might have copied the data incorrectly.  If that is the case, please check that there is nothing else incorrect before we all start chasing the wrong hare.....

---

### Post by spiky001 on 2010-07-07
A good idea would be to get a hub that way you can add more than 1 pc to the network

---

### Post by scanzano on 2010-07-07
I also found it kind of odd that both of the MAC addresses were identical, that seems to be issue number 1. Secondly how are you attempting to connect the two computers? If you are making an attempt at a direct connection then you would need a Crossover Cable (Modified version of an RJ45, these can be made with the proper tools or bought at a computer store). Personally I recommend that you use a standard switch,  and is it absolutely necessary that you have assigned them class B IP addresses (128.1.0.1 to 191.255.255.254)? Use a class C IP (192.0.1.1 to 223.255.254.254) to further simplify what you are trying to do so you don't have to mess around with the subnet mask too much.

---

