---
title: "Deluge + btguardproxy"
date: 2012-03-23
forum: General Help
---

### Post by yon2501 on 2012-03-23
! recently switched back to ubuntu from windows and just a small concern, when I used btguard with utorrent on windows it wouldnt let me seed at all, however on ubuntu using btguard with deluge it seeds as if theres no proxy. how can I check to make sure the proxy is being used for both incoming and outgoing p2p traffic?

---

### Post by gsgleason on 2012-03-23
Run a packet capture and set a filter for all traffic that is not going to proxy.btguard.com or whatever it is.

sudo apt-get install wireshark

gksudo wireshark

capture -> interfaces
click on start for the interface that has packet count incrementing.

As a display filter, use '!(ip.addr == x.x.x.x or ip.addr == y.y.y.y or ip.addr == z.z.z.z) make it as big as you need.

Each of those should be one of the addresses for the proxy server. 

Start capture.  This will show you all traffic

---

### Post by yon2501 on 2012-03-23
thanks seems like it isnt working so ill try the full encryption

---

### Post by gsgleason on 2012-03-24
This works and is easier.

tshark -i any -R '!dns' not host proxy.btguard.com

---

