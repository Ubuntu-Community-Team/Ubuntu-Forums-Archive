---
title: "Help for connection"
date: 2011-01-29
forum: General Help
---

### Post by angelofantalya on 2011-01-29
Hello, I have a problem with my external modem device. I must use at commands for connection but I cant reach connection. this is my connection profile wvdial.conf
Dialer Defaults]
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","mgb"
Modem Type : Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/tty8
Username = anonymous
Password = anonymous
Baud = 115200

and this is a commands which come with modem installation pdf
AT+CGDCONT=1,"IP","mgb"

and this is my connection failure notice

 Ignoring malformed input line: "Modem Type : Analog Modem"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

I dont know what is happening :(

---

### Post by angelofantalya on 2011-01-29
I think I cannot mount my serial device :(

---

### Post by Iowan on 2011-01-29
From a terminal (Applications>Accessories>Terminal):
 **sudo lshw** will provide information about your hardware. 
You can limit the results to communication devices by instead using **sudo lshw -C communication**.

---

