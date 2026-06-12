---
title: "CHAP Failure"
date: 2012-04-03
forum: General Help
---

### Post by VipinKV on 2012-04-03
I tried to connect a linux client to windows RAS. The authentication
protocol is CHAP . But I get a CHAP Failure in
the authentication phase. There is no mistake on the user name or
password. The same thing with MSCHAP (and also PAP as authentication
protocol)algorithm gets authenticated and works fine. 

Windows-2003 is the Remote Access Server.
LOG :

Apr  3 15:55:20 debian chat[17827]: abort on (ERROR)
Apr  3 15:55:20 debian chat[17827]: abort on (BUSY)
Apr  3 15:55:20 debian chat[17827]: abort on (NO CARRIER)
Apr  3 15:55:20 debian chat[17827]: abort on (VOICE)
Apr  3 15:55:20 debian chat[17827]: send (AT^M)
Apr  3 15:55:20 debian chat[17827]: expect (OK)
Apr  3 15:55:20 debian chat[17827]: ^M
Apr  3 15:55:20 debian chat[17827]: OK
Apr  3 15:55:20 debian chat[17827]:  -- got it
Apr  3 15:55:20 debian chat[17827]: send (ATDT5077^M)
Apr  3 15:55:20 debian chat[17827]: expect (CONNECT)
Apr  3 15:55:20 debian chat[17827]: ^M
Apr  3 15:55:46 debian chat[17827]: ^M
Apr  3 15:55:46 debian chat[17827]: CONNECT
Apr  3 15:55:46 debian chat[17827]:  -- got it
Apr  3 15:55:46 debian chat[17827]: send (^M)
Apr  3 15:55:46 debian chat[17827]: timeout set to 45 seconds
Apr  3 15:55:46 debian pppd[17815]: Serial connection established.
Apr  3 15:55:46 debian pppd[17815]: Using interface ppp0
Apr  3 15:55:46 debian pppd[17815]: Connect: ppp0 <--> /dev/ttyS0
Apr  3 15:55:48 debian pppd[17815]: **[FONT="Arial Black"]*CHAP authentication failed*[/FONT]**
Apr  3 15:55:49 debian pppd[17815]: Modem hangup
Apr  3 15:55:49 debian pppd[17815]: Connection terminated.
Apr  3 15:55:50 debian pppd[17815]: Exit.


What is the solution for this, Any help is appreciated

---

