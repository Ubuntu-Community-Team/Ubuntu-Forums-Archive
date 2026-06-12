---
title: "No Connection after Clean Install 12.04"
date: 2012-08-14
forum: General Help
---

### Post by Maynardus on 2012-08-14
Couldn't find a solution in existing threads, but I'm using a HP Pavilion tx2000 (I know) and recently did a fresh install and now I have no connectivity. This may be a simple/stupid fix but I need some help. I won't be online every day so don't worry if I don't fire back right away. Also, type slow, I'm noobish. 

When I check drivers under system settings I get error box: "Downloading package indexes failed, please check your network status." I have no proprietary drivers on my system. First problem. 

When I look under network, it says my cable is unplugged (it's not) but gives me a hardware address. That's probably to the lack of drivers. 

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a0:8a:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:448 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:448 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:36160 (36.1 KB)  TX bytes:36160 (36.1 KB) 

iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          
eth0      no wireless extensions. 


Please give me a hand!

---

