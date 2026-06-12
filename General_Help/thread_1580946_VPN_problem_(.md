---
title: "VPN problem :("
date: 2010-09-24
forum: General Help
---

### Post by SinaMiandashti on 2010-09-24
hi all

im REALLY new to linux and ubunto

i set up my connection to VPN server 1.allvpn.info
with my user and password
name of the connection "Sina"


it connect successfully ... but after short time ... for ex. 40 sec.
it disconnected with message : The VPN Connection 'sina' Failed

i dont know what is the problem
where the VPN error log stored so that i can check them?

UPDATE :  im using Ubunto Netbook Version

i found this logs :
```
Sep 24 12:37:17 sina-musicbase pppd[3484]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Sep 24 12:37:17 sina-musicbase pppd[3484]: pppd 2.4.5 started by root, uid 0
Sep 24 12:37:17 sina-musicbase pppd[3484]: Using interface ppp0
Sep 24 12:37:17 sina-musicbase pppd[3484]: Connect: ppp0 <--> /dev/pts/1
Sep 24 12:37:23 sina-musicbase pppd[3484]: Remote message: Login ok
Sep 24 12:37:23 sina-musicbase pppd[3484]: PAP authentication succeeded
Sep 24 12:37:28 sina-musicbase pppd[3484]: local  IP address 192.168.11.40
Sep 24 12:37:28 sina-musicbase pppd[3484]: remote IP address 94.76.231.17
Sep 24 12:37:28 sina-musicbase pppd[3484]: primary   DNS address 8.8.8.8
Sep 24 12:37:28 sina-musicbase pppd[3484]: secondary DNS address 4.2.2.4
Sep 24 12:37:51 sina-musicbase pppd[3484]: Modem hangup
Sep 24 12:37:51 sina-musicbase pppd[3484]: Connect time 0.4 minutes.
Sep 24 12:37:51 sina-musicbase pppd[3484]: Sent 7599 bytes, received 70856 bytes.
Sep 24 12:37:51 sina-musicbase pppd[3484]: Connection terminated.
Sep 24 12:37:51 sina-musicbase pppd[3484]: Exit.
```

---

### Post by SinaMiandashti on 2010-09-24
bump

---

