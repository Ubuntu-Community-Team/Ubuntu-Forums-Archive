---
title: "Problem getting internet to work - Network card not recognised?"
date: 2010-08-20
forum: General Help
---

### Post by Admiral Yi on 2010-08-20
Hi,
I have just set up a server with Ubuntu Server edition 10.04. I installed it by plugging the harddrive into my main pc as the server doesn't have a cd drive. Now the drive is back in the server and the internet won't work. I have run lspci and lshw and neither show a lan or network card anywhere. ifconfig comes up with nothing related to eth0, and says the 'inet addr' is 127.0.0.1. 

My motherboard has an onboard Realtek 8101L LAN controller. Can't seem to find much with a google search. Can anyone help?

---

### Post by Admiral Yi on 2010-08-20
I've managed to find another network card and plug that in, and that now shows up in lshw. However, it says disabled next to it and the internet still doesn't work. How can I get it enabled?

---

### Post by DamjanDimitrioski on 2010-08-20
> **Admiral Yi said:**
> I've managed to find another network card and plug that in, and that now shows up in lshw. However, it says disabled next to it and the internet still doesn't work. How can I get it enabled?
Open a terminal, or if you're in VT:
try:
```
ifconfig -a
```this will list your network interfaces.
if you're trying the internal network card, then it's eth0, and the new one is eth1, so you do:
```
sudo ifdown eth0
sudo ifup eth1
```then restart the network service, with:
```
sudo killall -9 NetworkManager
sudo NetworkManager
or
sudo /etc/init.d/networking restart

```

---

