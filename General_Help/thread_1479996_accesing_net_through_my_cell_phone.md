---
title: "accesing net through my cell phone"
date: 2010-05-11
forum: General Help
---

### Post by nbulchandani on 2010-05-11
Hello  everyone,
i just tried using my Nokia 2700 classic's internet on my Lynx.it got connected to the network when i ticked the option access internet via the phone in bluetooth setup.But i am unable to surf the net...I am still connected to my  college's wifi  network which uses a http proxy.I tried using no proxy in mozilla when i was connected to both the networks;but then also nothhing was working;whereas my cell showed the sign of GPRS...any ideas where i am wrong?
Thanks

---

### Post by 3rdalbum on 2010-05-11
Try what is suggested on this page regarding adding a DNS, this may be the reason why you can't find any sites when surfing through your phone:

[http://www.chrislees.info/ubuntu/opendns.shtml]("http://www.chrislees.info/ubuntu/opendns.shtml")

---

### Post by nbulchandani on 2010-05-11
well,that seems to be good info...but here the problem is my network is not listed there...Now what?
Thanks

---

### Post by zaphod777 on 2010-05-11
try disabling the wireless connection when doing it your computer can only use one default gateway and it is most likely sending all of the data through the wireless connection. 

Or you can try messing around with the iptables to have all of the http and https traffic go through the phone and everything else go through the wireless.

---

