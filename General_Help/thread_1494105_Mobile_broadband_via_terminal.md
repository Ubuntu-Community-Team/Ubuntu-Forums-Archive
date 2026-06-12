---
title: "Mobile broadband via terminal"
date: 2010-05-26
forum: General Help
---

### Post by spiky001 on 2010-05-26
OK I have a server that has the mobile broadband connection "ppp0" is there a way to turn it on and off via terminal, I have tried 
```
sudo ifconfig ppp0 up
```but not reconised 

Ifconfig shows connections for eth0 and l0 not ppp0 till it is connected
I,m sure this is possible, yes I know I can set it to auto connect but rather not

---

### Post by KeyserSoze93 on 2010-05-26
I managed to use wvdial with a T-Mobile USB dongle.

Not sure what make your mobile broadband is, but for me, I put the following in /etc/wvdial.conf

```


[Dialer Defaults]
Phone =
Username =
Password =
New PPPD = yes
[Dialer tmobileusb]
Phone = *99***1#
Username = web
Password = web
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","general.t-mobile.uk";

```

I could then run:

```
sudo wvdial tmobileusb
```

to connect.

---

### Post by spiky001 on 2010-05-28
Ok I,m not using wvdial my 3 broadband works straight from network manager can I use this some how and where would I put it

---

### Post by dino99 on 2010-05-28
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by spiky001 on 2010-05-28
Ok I have looked at the link have tried to edit my network interface similar to the link but still no luck can any one point me in the right direction,
> auto dsl-provider
iface dsl-provider inet ppp
        pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
        provider dsl-provider

I changed the eth1 for the the name in network manager "3 Internet"

---

### Post by spiky001 on 2010-05-30
bump

---

### Post by spiky001 on 2010-06-06
bump again

---

