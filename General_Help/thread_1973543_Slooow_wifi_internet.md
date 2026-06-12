---
title: "Slooow wifi internet"
date: 2012-05-04
forum: General Help
---

### Post by tricom on 2012-05-04
I have ubuntu 12.04 installed and my comcast internet wifi is terrible. I have to use ifconfig wlan0 down and then bring it back up, and for a minute or two it works fine and then it's slooow again or even stops working all together. I've searched the internet for help and nothing has worked. HELP !!!

---

### Post by carl4926 on 2012-05-05
Could it be IPv6 or DNS issue?

---

### Post by tricom on 2012-05-05
I have ipv6 disabled but maybe DNS idk

---

### Post by carl4926 on 2012-05-05
You didn't say if this was a new phenomena
Or are you new to Ubuntu

---

### Post by pqwoerituytrueiwoq on 2012-05-05
```
chad@chad-cq60-215dx:~$ ifconfig wlan0 | grep "inet addr" | sed 's/:/\n/' | tail -1 | sed 's/ /\n/' | head -1 
**10.0.0.**103
chad@chad-cq60-215dx:~$ ping **10.0.0.**1 -c 10 | grep loss
10 packets transmitted, 10 received, 0% packet loss, time 9000ms
```what do you get for loss?
change last number to a 1 from the 1st command
if you get over 0% (and you are close to your router as in with in a reasonable distance for the wireless to reach)
post the output of this
```
lspci | grep Ethernet
```

---

