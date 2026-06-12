---
title: "Dial-up fails after upgrade to Karmic"
date: 2009-11-13
forum: General Help
---

### Post by rayiam on 2009-11-13
My US Robotics USB modem worked perfectly under Ubuntu 9.04 but fails after upgrading to 9.10.  Basically, I can occasionally get dial up working by just doing random commands in a terminal (see the following), and it will continue to work until I power the T61 down.  However,dial up is again stone dead at the next power up.  I have spent several weeks on this problem and have run out of diagnostic ideas and flat just don't have a clue.

ray@T61:/usr/bin$ pon.wvdial
ray@T61:/usr/bin$ --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
^C
ray@T61:/usr/bin$ sudo pon.wvdialray@T61:/usr/bin$ pon.wvdial
ray@T61:/usr/bin$ --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
^C
ray@T61:/usr/bin$ sudo pon.wvdial
ray@T61:/usr/bin$ --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
^C
ray@T61:/usr/bin$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot get information for serial port. <========================== check this out! failed x times and then connected
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT499-9949
--> Waiting for carrier.
ATDT499-9949
CONNECT 24000/ARQ/V34/LAPM/V42BIS
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Nov 13 15:23:46 2009
--> Pid of pppd: 2342
--> Using interface ppp0
--> pppd: `F&#65533;[08][10]F&#65533;[08]
--> pppd: `F&#65533;[08][10]F&#65533;[08]
--> pppd: `F&#65533;[08][10]F&#65533;[08]
--> pppd: `F&#65533;[08][10]F&#65533;[08]
--> pppd: `F&#65533;[08][10]F&#65533;[08]
--> pppd: `F&#65533;[08][10]F&#65533;[08]
--> pppd: `F&#65533;[08][10]F&#65533;[08]
.
.
.
.
Thanks for any insight.

---

### Post by coldReactive on 2009-11-13
possible that the package wvdial requires full hal support, which is removed.

---

### Post by DustStuff on 2010-03-01
This post does not really refer to most (or all?) of what people have been posting here, but it does refer to the subject of this thread.

If you are using a USB modem and were using wvdial (or possibly another dialer) successfully in Ubuntu 9.04, but it no longer works (with the same settings) in Ubuntu 9.10, then you might want to check out [this post]("http://ubuntuforums.org/showthread.php?p=8899463#post8899463") for a workaround solution.

---

