---
title: "How to connect to pureftp"
date: 2011-11-27
forum: General Help
---

### Post by newellj79 on 2011-11-27
I setup pureftp on my 11.10 box so that i can transfer files to my android device.  I can't find what the address is to connect to the server though.   Please help...

---

### Post by The Cog on 2011-11-27
The command **ifconfig** will print out lots of info about your interfaces, including your IP address. Note that it you are behind a Network Address Translating router, the address that ifconfig gives you is your local LAN address, not the address seen by the rest of the internet.

---

### Post by gandaran on 2011-11-27
> **newellj79 said:**
> I setup pureftp on my 11.10 box so that i can transfer files to my android device.  I can't find what the address is to connect to the server though.   Please help...
do you have one of those FTP _server_ apps from the market installed on the android device?
this app is needed to make the device work as FTP server
then the FTP server app when you start it shows the FTP IP address to type in the computer FTP client or any web broswer url bar.

edit
I have read your post again and only noticed now that PureFTP is a server not client application, sorry about that but I still think that using a FTP server app on the android device and a FTP client on the computer (Filezilla is nice) is the best and easy way to transfer files locally.
If you still prefer using the computer as server (and access files remotely anywhere) then I would recommend signing up to a free dynamic DNS service like DynDNS

---

### Post by newellj79 on 2011-11-27
> **The Cog said:**
> The command **ifconfig** will print out lots of info about your interfaces, including your IP address. Note that it you are behind a Network Address Translating router, the address that ifconfig gives you is your local LAN address, not the address seen by the rest of the internet.

thanks I will check when I get home. I am on a wireless router. if ipconfig doesn't show the right address do u know how I can find it?

---

### Post by gandaran on 2011-11-27
> **newellj79 said:**
> thanks I will check when I get home. I am on a wireless router. if ipconfig doesn't show the right address do u know how I can find it?
ifconfig (attention not ipconfig, ipconfig is the windows command version) will show the the router IP assigned to your computer and that is exactly what you need plus the 21 port, so the address to connect on the android device (local network only) should be something like this
```
ftp://192.168.1.101:21/
```
192.168.1.101 is my router computer IP check if yours match.

---

### Post by newellj79 on 2011-11-27
> **gandaran said:**
> ifconfig (attention not ipconfig, ipconfig is the windows command version) will show the the router IP assigned to your computer and that is exactly what you need plus the 21 port, so the address to connect on the android device (local network only) should be something like this
```
ftp://192.168.1.10i:21/
```
192.168.1.10 is my _router computer IP_ check if yours match.

thank u friend. will try this evening and report back.

---

### Post by newellj79 on 2011-11-27
This is what i get with ifconfig:

th0      Link encap:Ethernet  HWaddr 00:24:be:7d:a8:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:180179 (180.1 KB)  TX bytes:180179 (180.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:35:d2:cc  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe35:d2cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12842981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9343212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15374258947 (15.3 GB)  TX bytes:2316112576 (2.3 GB)

i tried both the 127... and 10... it says no server found at both.

---

### Post by gandaran on 2011-11-27
click on the panel network icon » connection information » IP address, that's the one you should use.

---

### Post by newellj79 on 2011-11-27
> **gandaran said:**
> click on the panel network icon » connection information » IP address, that's the one you should use.

yep got it. now its saying I'm.trying to use the wrong password though.  I've checked and changed it several times. Grrrr. ill mess with it later. thanks again.

---

### Post by Dry Lips on 2011-11-27
If you're behind a NAT router you also have to forward the port that
your FTP server use. (Usually port 21) You normally have to access
the setup of your router in order to do this.

---

