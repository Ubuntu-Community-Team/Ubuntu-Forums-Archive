---
title: "NetworkManager hangs on WEP authentication attempt"
date: 2011-10-12
forum: General Help
---

### Post by robbiemacg on 2011-10-12
Hi all,
I'm traveling on business, having some serious difficulty connecting to a generic, WEP protected wireless network. Every time I type out the key and try to "connect" using the NetworkManager GUI, it hangs.
I'm trying to connect to a generic router provided by the local telco. The ESSID is just BELL877, the key it requires is 128 bit string of digits. 
I've stayed here before, connected to similar networks, have never experienced this kind of issue.

Anyway, yeah, I'm on 11.04. **iwconfig** seems to return sensible information about both the network and my wireless radio. Are there other commands I could run/post results?

Here are the relevant lines from my  **iwconfig** result:
```
wlan0     IEEE 802.11abgn  ESSID:"BELL877"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: B0:E7:54:A8:CE:A1   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-21 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0

```Thanks in advance for your help/feedback. Hopefully I'll be unwired soon. :(

---

### Post by robbiemacg on 2011-10-12
I'm not entirely satisfied (still unclear what caused the problem), but I was able to authenticate by connecting to the router via ethernet and then attempting to establish a wireless connection. IDK.

I'll leave this thread open a little longer in case someone has useful feedback for me, can help me avoid similar problems in future. I'll give the old [SOLVED] flag this p.m.

Thanks again,
Robbie

---

