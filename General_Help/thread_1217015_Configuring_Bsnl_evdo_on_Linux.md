---
title: "Configuring Bsnl evdo on Linux"
date: 2009-07-19
forum: General Help
---

### Post by charanpreethu on 2009-07-19
Hi,
   I am using mint gloria.How to configure bsnl evdo on it.I googled for the solution and followed some steps but it didnt work.Here are the steps

1)downloaded and installed wvdial
2)In command line I used wvdialconf to create wvdial.conf file
3)deleted the contents of /etc/wvdial.conf and redited it as
    Modem=/dev/ttyUSB0
    Baud=115200
    Dial Command = ATDT
    Baud=115200
    Dial Command = ATDT
    init1=ATZ
    init2=AT+CRM=1
    Flow Control= Hardware (CRTSCTS)
    Username = <your username>
    Password = <your password>
    Phone = #777
    Stupid Mode = 1 
4)typed wvdial in terminal.


Errors I got

1)modprobe usbserial vendor=0×19d2 product=0×fffe-
  this command didnt work.I got vendor and product using lsusb.

2)When I used wvdial command to connect to internet I got pppd daemon died.


Pls help me

---

### Post by jonobr on 2009-07-19
Maybe this is unique to India , but I dont get something here.

EVDO is evolution data optimized,

its a wireless broadband access technology (CDMA2000)

Maybe I am just missing how its done in Ubuntu. but what you are decribing below looks like a regular pots line PPP connection and not evdo.

Again, maybe IM getting the wrong end of the stick here.

---

### Post by charanpreethu on 2009-07-19
so what is the solution for my problem???

---

### Post by jonobr on 2009-07-19
wow


Thanks for the response outlining what EVDO is in India and that its not dialup.
Truly a great technical dialogue

Greatly appreciate your sharing.

[Heres ]("http://http://abhisheknagar.com/blogs/configuring-bsnl-evdo-modem-debian-gnulinux")the VERY first hit i got in google showing your init2 is different
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
and the stupid mode is set to on not 1.


This is for a ZTe modem. Seeing as how you didnt mention hardware I have no idea if this relates.

This may be relevant to your setup and then again maybe not,
but given your self serving attitude, I dont care

---

