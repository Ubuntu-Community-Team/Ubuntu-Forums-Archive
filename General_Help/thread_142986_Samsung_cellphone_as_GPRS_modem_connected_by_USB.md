---
title: "Samsung cellphone as GPRS modem connected by USB"
date: 2006-03-11
forum: General Help
---

### Post by mindless on 2006-03-11
I'm trying to dial up using my cellphone. Ubuntu seems to detect my phone as lsusb shows:
```
Bus 001 Device 004: ID 04e8:663e Samsung Electronics Co., Ltd
```

On windows I use it and dial in with no username or password, can this be done? Here is the log I get.. the tool I'm using is gnome-ppp which detects my modem at /dev/ttyACM0.
```
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
NO CARRIER
ATX3
OK 
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATX3
ATX3
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Please enter password (or empty password to stop):

```

I'm a linux noob so please tell me if any more information is needed.

---

