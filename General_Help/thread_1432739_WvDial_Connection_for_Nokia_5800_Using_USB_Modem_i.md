---
title: "WvDial Connection for Nokia 5800 Using USB Modem in 9.10"
date: 2010-03-18
forum: General Help
---

### Post by somepalli on 2010-03-18
HI,

I am trying connect to internet using Nokia 5800 Xpress music in Ubuntu 9.10. 
The following steps are i followed to configure Nokia 5800 using WvDial

1) Making the new connection using as follows

  >  sudo wvdialconf /etc/wvdial.conf
2) then i got following 
Editing `/etc/wvdial.conf'.
> 
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- Nokia
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

> sudo gedit /etc/wvdial.conf

3) These are the my wvdial.conf

> [Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Stupid Mode = 1
Phone = *99#
Username = username
Password = password
New PPPD = yes

4) the following command i used to connect my mobile 

> sudo wvdial

> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Mar 18 14:20:50 2010
--> Pid of pppd: 5928
--> Using interface ppp0
--> pppd: &#65533;6[06]  7[06] 
--> pppd: &#65533;6[06]  7[06] 
--> pppd: &#65533;6[06]  7[06] 
--> pppd: &#65533;6[06]  7[06] 
--> pppd: &#65533;6[06]  7[06] 
--> pppd: &#65533;6[06]  7[06] 
--> Disconnecting at Thu Mar 18 14:20:54 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

5) then i checked my log message. the following message its showing.

> Mar 18 14:12:54 chow pppd[5694]: pppd 2.4.5 started by root, uid 0
Mar 18 14:12:54 chow pppd[5694]: Using interface ppp0
Mar 18 14:12:54 chow pppd[5694]: Connect: ppp0 <--> /dev/ttyACM0
Mar 18 14:12:54 chow pppd[5694]: PAP authentication succeeded
Mar 18 14:12:55 chow pppd[5694]: LCP terminated by peer
Mar 18 14:12:58 chow pppd[5694]: Connection terminated.
Mar 18 14:12:58 chow pppd[5694]: Modem hangup
Mar 18 14:12:58 chow pppd[5694]: Exit.
Mar 18 14:13:07 chow pppd[5701]: pppd 2.4.5 started by root, uid 0
Mar 18 14:13:07 chow pppd[5701]: Using interface ppp0
Mar 18 14:13:07 chow pppd[5701]: Connect: ppp0 <--> /dev/ttyACM0
Mar 18 14:13:08 chow pppd[5701]: PAP authentication succeeded
Mar 18 14:13:08 chow pppd[5701]: LCP terminated by peer
Mar 18 14:13:11 chow pppd[5701]: Connection terminated.
Mar 18 14:13:11 chow pppd[5701]: Modem hangup
Mar 18 14:13:11 chow pppd[5701]: Exit.

[COLOR="Blue"]My Service Provider is TATA DOCOMO GSM (India)
Please help regarding this. How to solve this.[/COLOR]

---

### Post by yhcheang on 2011-02-14
Add this line to your /etc/wvdial.conf:

Init3 = AT+CGDCONT=1,"IP","*APN*","",0,0

Please change *APN* to your access point name, for example my Airtel India is using airtelgprs.com as APN.

So my complete statement would be like this:

Init3 = AT+CGDCONT=1,"IP","airtelgprs.com","",0,0

Hope it helps;)

---

