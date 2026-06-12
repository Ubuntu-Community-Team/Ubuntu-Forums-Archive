---
title: "Wireless Network Problem"
date: 2010-09-08
forum: General Help
---

### Post by shinfusion on 2010-09-08
Hello All. I'm having a problem with my network card and router interacting. I just did a fresh install of Ubuntu 10.04 LTS 3 days ago and until yesterday had no problems whatsoever. Whenever I start the connection to the router, It connects fine and will load maybe 1 or 2 web pages then proceeds to hang. I don't know any other way to fix this other than to reset the router but every time I do that, It just ends up doing the same thing. I have searched for threads with the same problem to no avail. There are two other computers on the same network, both running Vista. They have no problems. Please help. I've been working on this for the last 4 hours and am getting tired. 

I'm running Ubuntu 10.04 LTS x86-64 on Asus laptop UL50AG with Belkin N router
iwconfig is as follows:

drew@drew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Belkin N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:75:4C:C6:97   
          [COLOR=Red]Bit Rate=11 Mb/s[/COLOR]   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and then a moment after:

drew@drew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Belkin N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:75:4C:C6:97   
          [COLOR=Red]Bit Rate=0 kb/s[/COLOR]   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

As I said before, everything was working fine 2 days ago, then all of the sudden this happened. By the way, my computer will connect wirelessly to other local routers fine. No hang ups. Thanks for your help.

---

### Post by TruViet911 on 2010-09-08
is your network interface build in? i just install ubuntu on my laptop too. no problem at all. might be your brower cause to hang up?

---

### Post by shinfusion on 2010-09-08
Yes, the network card is built in. I don't think its the browser, because it works fine when connected to another router.

---

### Post by shinfusion on 2010-09-09
For some reason, I just needed to revert the router settings to factory and restart my computer. I believe that the UPnP feature on my router caused the problem. That's the only explanation I have.

---

