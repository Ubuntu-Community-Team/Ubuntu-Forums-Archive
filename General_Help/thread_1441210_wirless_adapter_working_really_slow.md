---
title: "wirless adapter working really slow"
date: 2010-03-28
forum: General Help
---

### Post by panti19 on 2010-03-28
i have a desktop with ubuntu 9.10 and i can't use ethernet so i must stick to my wireless connection.

i have two usb wireless adapters, both are recognized by ubuntu and find my wirless network but they work painfully slow..and often disconnect. The signal is good, because i'm now typing from an eee pc with ubuntu from the same location.

what to do?

one wireless adapter is:TP-LINK TL-WN321G
the other: Trendnet TEW-424UB
thanks

---

### Post by panti19 on 2010-03-28
please help, i really need to make this pc usable.

---

### Post by stringtheorem on 2010-03-28
What do you get from a iwconfig in the terminal.

This should tell you the bit rate of the wireless connection.

---

### Post by panti19 on 2010-03-28
wlan2     IEEE 802.11bg  ESSID:"JMG LINK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0:7D:E0:30   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-15 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i don't understand..now it's working fine. but i'm afraid it will do it again.
i am using the trendnet adapter.
i'm gonna follow this:
[http://ohioloco.ubuntuforums.org/showthread.php?t=529090](http://ohioloco.ubuntuforums.org/showthread.php?t=529090)

---

### Post by stringtheorem on 2010-03-28
The link you posted is to install NDisWrapper.

I found this on the forums with a guy who had a similar problem but with a Broadcom adapter. [http://ubuntuforums.org/showthread.php?t=839817]("http://ubuntuforums.org/showthread.php?t=839817")

If its working ok, its probably ok to carry on using it. If you have any other problems, perhaps have a look at NDisWrapper.

---

