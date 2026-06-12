---
title: "Wireless Won't Connect with Ubuntu"
date: 2011-04-09
forum: General Help
---

### Post by EarthBoundX5 on 2011-04-09
So I recently installed Ubuntu 10.10 on a secondary harddrive in my desktop, and immediately ran into a very strange problem I cannot solve.  The wireless will not connect to my access point.

I use static routing (ie, DHCP is disabled), and configured the static IP to be the same as it was in Windows; as I have the IP addresses saved in my router to MAC addresses for whenever I need to temporarily turn DHCP on (but mostly, its just so I have a list of all my devices).

Anyways, when i select my wireless connection, it just keeps showing its connecting then finally disconnects.  This is driving me crazy.

Here is some misc info if needed....
*Network Tools displays the correct MAC address for the card
*Its a PCI-E 802.11n by Lite-On/Ralink

Here is my output for ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:ec:95:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9024 (9.0 KB)  TX bytes:9024 (9.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:cf:0c:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Here is my output for iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"netgear-g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=2 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Thanks in advance.

---

### Post by EarthBoundX5 on 2011-04-10
Hmm, I'm surprised there has been no response yet?  Well to avoid this just being a bump, I guess I will ask if their is ANY more information I should provide that would make anyone viewing this more able to assist me?

I am going to try 10.04, see if it has the same problem.  I am sure there will be no difference, but its better then just waiting around.  After reinstall, I will repost updated info if there is any changes from what I already posted.

EDIT: And I just realized, sorry for not mentioning, but I am using 64-bit versions of Ubuntu (desktop, not alternative if I remember) if that at all matters.

EDIT 2: Wow, guess it was a problem with 10.10.

EDIT 3: Works fine after upgrading to 10.10 from 10.04.

---

