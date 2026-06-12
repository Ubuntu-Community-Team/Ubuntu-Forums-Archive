---
title: "Ad Hoc not working - (network isn't created for public access)"
date: 2011-08-03
forum: General Help
---

### Post by micael3000 on 2011-08-03
Hello,

Today I was creating an Ad Hoc network for sharing internet connection and I realized it is not working... I have done it before on Ubuntu 10.10, now on 11.04 it just doesn't work. I create a new connection (Create New Wireless Network) and it is never visible to the other computers (I checked the IPv4 settings, it was Shared to Other Computers).

I really do not know what is going on, my wireless card is working perfectly fine (I can connect to other network and on additional driver it is there with a green circle)...

Any help will be welcome!

Thank you :)

---

### Post by Kira_Belka on 2011-08-03
> **micael3000 said:**
> Hello,

Today I was creating an Ad Hoc network for sharing internet connection and I realized it is not working... I have done it before on Ubuntu 10.10, now on 11.04 it just doesn't work. I create a new connection (Create New Wireless Network) and it is never visible to the other computers (I checked the IPv4 settings, it was Shared to Other Computers).

I really do not know what is going on, my wireless card is working perfectly fine (I can connect to other network and on additional driver it is there with a green circle)...

Any help will be welcome!

Thank you :) mb model of wifi card at first. it'll be a bit easier to help

---

### Post by micael3000 on 2011-08-04
Hello,

It is "Dell Wireless™ 1397 Half Mini Card (802.11g)".

Thanks.

---

### Post by micael3000 on 2011-08-07
Bump :|

---

### Post by micael3000 on 2011-08-09
Double bump! :)

---

### Post by micael3000 on 2011-08-10
Triple Bump! :|

---

### Post by micael3000 on 2011-09-11
Since nobody seems to know what is wrong I will close this topic very soon.

---

### Post by spiky001 on 2011-09-11
I have found the same problem, I found that the machine with the Ad hoc connection had tp be connected to the connection which was hiddden. When the connection was made it was then visible on the network.

---

### Post by mrcoolinux on 2011-09-11
Hi. This may sound like a dumb Question!!!
But did you Reboot? After Create New Wireless Network.

---

### Post by spiky001 on 2011-09-11
If you check lwconfig when you start the machine I suspect the wlan will say MODE MANAGED and not MODE ADHOC. It is starting in the wrong mode.

---

