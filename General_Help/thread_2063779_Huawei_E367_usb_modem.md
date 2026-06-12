---
title: "Huawei E367 usb modem"
date: 2012-09-27
forum: General Help
---

### Post by nokia443 on 2012-09-27
Hey, i'm a newbie at ubuntu and just installed ubuntu 10.04 LTS on a duel boot with windows using wibu its not automatically detecting the modem.
 
I typed lsusb (which i got off another topic) but couldn't get any further
 
Bus 003 Device 003: ID 10f5:0242 Turtle Beach 
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
be great if you could help thanks :-)

---

### Post by jerrrys on 2012-09-27
Looks like some fixes [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Huawei+E367&as_qdr=all&sa=Google+Search&lang=en")

And welcome to the forums :)

---

### Post by nokia443 on 2012-09-27
says download modeswitch dont have access to internet on that machine.

---

### Post by jerrrys on 2012-09-27
There are several ways to download packages for offline use.  I have not used them, but I do use synaptic and that is one way.  It can also be done on a windows machine.  I think (if you want to go this route) it would be better to start a new thread on offline downloads and get input from users experience with this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+packages+offline&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+packages+offline&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by alexfish on 2012-10-01
Hi

The latest range of Huawei devices are better supported in 12.04

have tested some on 12.10 development beta , looking good since all parts of the device are configuring . IE Supported. say he I think.

If new to Ubuntu then suggest trying 12.04 .Then try 12.10  . Final release is due 18 OCT , here I would suggest trying with Live CD first


Compare the device with this command from the terminal

```
usb-devices
```Regards

alexfish

ADDED ; for latent support then suggest sakis3g
**[*Sakis3G* - All-in-one script]("http://www.sakis3g.org/")**


but not recommended for Ubuntu > 10.04 , due to different configs in the usb_modeswitch

---

