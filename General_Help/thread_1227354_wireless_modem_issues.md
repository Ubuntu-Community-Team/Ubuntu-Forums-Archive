---
title: "wireless modem issues"
date: 2009-07-30
forum: General Help
---

### Post by unix1adm on 2009-07-30
I have it working but sometimes it will not reconnect and I have to logout and back in to get it to work. I tries to connect but then just says offline. 

really annoying as I use it off and on and dont want to leave it connected all the time.

---

### Post by unix1adm on 2009-07-31
I want to know what broke on the original setup. It was fine. Then some code must have been updated. I know i saw several packages the other day that needed to be updated for security reasons and now my wireless only works if i log out and back in.

OK something really strange here for you guys....

I start a terminal window to get cmd access. I dont do anything but su - to get into root.
I disconnect the wireless and it wont reconnect.
I just happen to close the terminal window and it says there is a running process. I did not start anything in the window. Just a cmd prompt.

So i kill the window and tried the wireless connection again and it reconnected.

More trouble shooting... I started up a window but did not su - to root. I can connect the wireless modem fine.

I su - in the terminal window and try to connect. No connection. I logout of root and leave my regular user in the terminal window and now i can reconnect to wireless.

So it would seem it has something to do with a root login. But why is the question would a root login on a terminal window prevent wireless from working.

---

### Post by afeasfaerw23231233 on 2009-07-31
Is that a wireless router instead of modem? It is quite strange. Would you please post the output of ifconfig and iwconfig?

---

### Post by unix1adm on 2009-08-03
Not a router but a verizion wirless card. Ill get the output you request shortly.

---

### Post by unix1adm on 2009-08-03
ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0e:9b:bf:a5:8f  
          inet6 addr: fe80::20e:9bff:febf:a58f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:11:25:86:3d:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3664 (3.6 KB)  TX bytes:3664 (3.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.250.4.122  P-t-P:66.174.168.192  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:16149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16603334 (16.6 MB)  TX bytes:2772345 (2.7 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-0E-9F-BF-A5-8B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100693 errors:0 dropped:0 overruns:0 frame:9633
          TX packets:1205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:11587478 (11.5 MB)  TX bytes:55430 (55.4 KB)
          Interrupt:11 

cj454@cj454-lt:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:98689  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by unix1adm on 2009-08-05
bump to top.. no one has had this issue?

---

### Post by unix1adm on 2009-08-10
anyone at all have this happen to them

---

### Post by unix1adm on 2009-09-14
im still trying to find a solution for this.

---

