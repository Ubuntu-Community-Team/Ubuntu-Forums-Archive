---
title: "network address"
date: 2010-03-01
forum: General Help
---

### Post by junke1990 on 2010-03-01
hey guys is there any file or so where I can find the network address? so not the IP or gateway or so but

ip 192.168.1.2
netmask 255.255.255.0
**network adress 192.168.1.0**

or is there a simple bash script to calculate this from the IP address?

---

### Post by Danawar on 2010-03-01
Not sure if this is the reply you are looking for but if you open terminal and type ifconfig it gives you information similar to IPCONFIG in windows.

-Dan

---

### Post by emanuel.b on 2010-03-01
You could try "System -> Administration -> Network Tools"...

---

### Post by junke1990 on 2010-03-01
i need it for a bash script to set the iptables

---

### Post by Danawar on 2010-03-01
Ahhh im not that advanced yet not sure if this will help though **[http://www.howtoforge.com/linux_iptables_sarge](http://www.howtoforge.com/linux_iptables_sarge) **Sorry i cant be of more assitance.

-Dan

---

### Post by bodhi.zazen on 2010-03-01
I would suggest you set a static IP address =)

---

### Post by junke1990 on 2010-03-01
it's for bridging to networks so I can connect to my wireless which is turned in to an AP and the data will be put through my 3G adapter.

so it will be dynamic all the time...

---

