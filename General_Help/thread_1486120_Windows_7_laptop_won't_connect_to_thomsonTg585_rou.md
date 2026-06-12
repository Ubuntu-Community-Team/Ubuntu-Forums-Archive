---
title: "Windows 7 laptop won't connect to thomsonTg585 router, but ubuntu and xp can."
date: 2010-05-17
forum: General Help
---

### Post by Mr_VeRiTy on 2010-05-17
Hi, I am using ubuntu lucid and am able to connect to my ThomsonTG585 wireless router, but my mother who uses win7 is unable to connect, except by Ethernet cable, which is not convenient, how can I get her connected.

When I try to connect, It it says "limited connectivity" and does not let her utilize the internet.

My brother is dual booting ubuntu karmic and winXP and is able to connect on both os's.

I am absolutely sure I am entering the correct pass-phrase and ssid.


please help.

---

### Post by dementic on 2010-05-17
Is it the same laptop? Is there a mac filtering on the router? Otherwise try to update the drivers and make sure that the connection settings are on auto (not a predefined ip for exemple).

---

### Post by Mr_VeRiTy on 2010-05-17
When you say "is it the same laptop" if you mean are me and my mother using the same laptop, no and I don't know what mac filtering is, i'm not very technical :P

---

### Post by soltanis on 2010-05-17
Sounds like a Windows 7 problem and not a router problem. But just to confirm, please post the output of

```

ifconfig

```

From your Ubuntu system, from a terminal. Did you change any of the settings in the router when you were setting it up? Can other people bring their computers and connect to your router just fine?

---

### Post by Mr_VeRiTy on 2010-05-17
the output was

```
luke@luke-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:e0:6a:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:299551 (299.5 KB)  TX bytes:299551 (299.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:21:cf:72:e2  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fecf:72e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114540 errors:0 dropped:139161 overruns:0 frame:0
          TX packets:87942 errors:405 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144290617 (144.2 MB)  TX bytes:13960655 (13.9 MB)
          Interrupt:17 Memory:f80b0000-f80b0100 

luke@luke-laptop:~$ 

```And my sister, who also uses ubuntu, can connect using her laptop

And I don't think I edited any settings, as the router was pretty much out-of-the-box.

---

### Post by Mark Phelps on 2010-05-17
> **Mr_VeRiTy said:**
> Hi, I am using ubuntu lucid and am able to connect to my ThomsonTG585 wireless router, but my mother who uses win7 is unable to connect, except by Ethernet cable, which is not convenient, how can I get her connected.

Is this a Win7-specific problem?  IF so, you should post to sevenforums.com -- the finest Win7 forum out there.

---

### Post by Mr_VeRiTy on 2010-05-17
sevenforums.com aren't responding too fast, anything I could do to get it working on win7

---

