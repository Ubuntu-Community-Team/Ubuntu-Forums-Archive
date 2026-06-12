---
title: "network icon gone"
date: 2010-07-06
forum: General Help
---

### Post by even.raghu on 2010-07-06
hi
need help?

i install ubuntu 10.04LTS yesterday, everything going fine.. i install latest nvidia driver, listen music and connect internet.

i use adsl modem.. and using
DSL Modem Config:
Install = sudo pppoeconf or sudo apt-get install pppoeconf
Connect = sudo pon dsl-provider
Disconnect = sudo poff

everything going fine.. but when today i power on pc, the network icon gone. in network connection there is no eth0.. but in ifconfig eth0 its shows... can access internet

plz help me how i back my network icon and connect internet?

---

### Post by even.raghu on 2010-07-06
[IMG]http://i45.tinypic.com/wvstjb.png[/IMG]

[IMG]http://i47.tinypic.com/33uwg15.png[/IMG]

---

### Post by fetuspuppet on 2010-07-06
What happens when you try


sudo dhclient /dev/eth0


Thanks!

---

### Post by philinux on 2010-07-06
[http://ubuntuforums.org/search.php?searchid=74378594](http://ubuntuforums.org/search.php?searchid=74378594)

---

### Post by dineshs on 2010-07-06
In a terminal type
```
gksudo gedit /etc/network/interfaces 
```and enter.
comment out all lines(put a # before each line)[COLOR="Blue"]except[/COLOR] the following 
```
auto lo
iface lo inet loopback
```
Restart the machine.If NM icon is back configure DSL via NM and[COLOR="Blue"] not [/COLOR]*pppoeconf* command ie
Right-click on the NM icon and then click on Edit Connections- DSL tab-add and proceed.tick [COLOR="Blue"]available to all users[/COLOR] while configuring.

---

### Post by even.raghu on 2010-07-06
guyz i solve this problem... this is due to tht dam pppoeconf command.. 

dinesh dude thanks... now i can connect internet by use dsl menu which is very simple..
thanks man....

---

