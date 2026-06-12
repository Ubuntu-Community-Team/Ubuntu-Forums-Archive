---
title: "Power outage -- Now net wont' work, no way"
date: 2006-05-15
forum: General Help
---

### Post by charliejohn on 2006-05-15
I just installed the latest version clean. I'm on a wireless router, with the Ubuntu plugged into a wired connected. Two Windows machines are on the same network, plugged in the same way.
We had a very brief power outage -- two seconds at most -- and now this machine will NOT go back on the network. The Windows machines work fine.
Tried:
Turning router off and on
New network cable from Ubuntu machine to router
Turning network card off and on ... 
Rebooted machine (turned off too) multiple times ...
I'm out of ideas?
Anyone who can tell me something else to do?
thanks
charlie

---

### Post by Omnios on 2006-05-15
try 

 ```

ifconfig etho down
ifconfig etho up

```

 Mine is set up as eth0 yours might be different, its basicly about the same equivalent as ipconfig in wondows. 

 It might have something to do with the router as some reset after a power outag, I actualy had this done to me once and had to unplug the modem and router for just over a min to get my network working. Also antoher thing to check is the network config in Ubuntu to see if it set at the right address for your router plug

---

