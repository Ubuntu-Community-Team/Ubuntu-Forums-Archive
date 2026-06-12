---
title: "canon LBP5050 oe not work"
date: 2011-08-03
forum: General Help
---

### Post by Valentin630 on 2011-08-03
According to 
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)
I have installed driver
All corresponds to the manual, only the printer does not work.
The status monitor works fine.
there is a small difference between document and my case:
root@maxt:~# /etc/init.d/ccpd status
/usr/sbin/ccpd: 15650 15645
according to the document should be:
Canon Printer Daemon for CUPS: ccpd: 15650 15645
The problem is: I see that the job is created but it does not appear in the print queue

Thanks in advance

---

