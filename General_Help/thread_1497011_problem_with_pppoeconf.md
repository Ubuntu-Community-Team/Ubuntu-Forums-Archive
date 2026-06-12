---
title: "problem with pppoeconf"
date: 2010-05-30
forum: General Help
---

### Post by tanixmukherzee on 2010-05-30
hi
i earlier used bsnl broadband in ubuntu and configure it using  pppoeconf. right now i shifted to reliance broadband(not usb  modem) but  now pppoeconf cannot detect the connection

It shows something like " Sorry I scanned two interfaces but the access  concentrator of ur provider did not respond.plz chck ur ntwrk and modem  cables. anoder reason fir the scan 
failure may be anoder running pppoe process which controls the modem"

what to do...
can nebody suggest ?

---

### Post by dineshs on 2010-05-30
If you are using ethernet port for connecting modem,pl post the output of
```
ifconfig -a
```
Also what do you get when you ping 4.2.2.1?
```
ping 4.2.2.1 -c5
```

---

