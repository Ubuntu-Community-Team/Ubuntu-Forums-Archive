---
title: "Cisco VPN IPsec - Gnome NetworkManager - Time Outs"
date: 2009-09-29
forum: General Help
---

### Post by ksudbury on 2009-09-29
Hi Guys, 

I am using Gnome NetworkManager to handle IPSec VPN connections and for some reason it keeps timing out on my Ubuntu desktop, I don't get this problem on my mac or my xp machines, so it is not the VPN server any ideas? 

TIA

---

### Post by pawhtiobo on 2009-09-29
Hi :)
 
Which software do you use associated with Gnome Network Manager? vpnc or other?
 
see ya...

---

### Post by ksudbury on 2009-09-29
I am using the gnome Network-Manager applet with vpnc.

---

### Post by pawhtiobo on 2009-09-29
Hi :)
 
Have you tested the vpnc options:
 
[http://t3.gstatic.com/images?q=tbn:SLwzJFmozN_v7M:http://1.bp.blogspot.com/_6NW5KdopjUM/SGRlk6w3zpI/AAAAAAAAAEU/4zxEWYuDAYs/s400/Ubuntu_VPNC.png](http://t3.gstatic.com/images?q=tbn:SLwzJFmozN_v7M:http://1.bp.blogspot.com/_6NW5KdopjUM/SGRlk6w3zpI/AAAAAAAAAEU/4zxEWYuDAYs/s400/Ubuntu_VPNC.png)
 
Disable NAT traversal
Enable weak single DES encryption
Allow using NULL encryption
 
For me to connect to some work sites i have to change some of these options, you can also import your *.pcf file that you use in windows (cisco VPN).
 
I hope that can help,
 
see ya...

---

### Post by ksudbury on 2009-10-13
I have tried editing the settings, that .png you posted was to small to view! 

I still seem to get drop outs about every hour, which is annoying and forcing me to use my MacBook...

---

