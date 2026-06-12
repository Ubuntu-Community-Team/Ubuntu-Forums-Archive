---
title: "Help please no Internet WVDIAL / 3G Dongle"
date: 2009-11-28
forum: General Help
---

### Post by markytheone on 2009-11-28
Hi guys, I have setup my ubuntu Hardy server to connect to the Internet using wvdial. It has worked fine for many weeks but now suddenly when I run "wvdial tmobile" I get this error:

--> Pid of pppd: 3334
--> Using interface ppp0
--> local  IP address 10.217.9.32
--> remote IP address 10.64.64.64
--> primary   DNS address 149.254.192.126
--> secondary DNS address 149.254.201.126
--> Connect time 0.0 minutes.
--> Disconnecting at Sat Nov 28 11:50:07 2009

It connects but instantly disconnects.

My wvdial.conf file looks like this:

[Dialer defaults]
Modem = /dev/ttyUSB1

[Dialer tmobile]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99\#
Modem = /dev/ttyUSB0
username = user
Password = one2one
Dial Command = ATDT
Baud =466600
Init4 = AT+CGDCONT=1,"IP","general.t-mobile.uk"


Any help would be greatly recevied.

Thanks

Mark

---

### Post by markytheone on 2009-11-28
Guys this is really important. If anyone has any tips or pointers I would be externally greatfull!

I have tried google and searching these forums but nothing.

Mark

---

