---
title: "who start apache??"
date: 2010-10-19
forum: General Help
---

### Post by issamneo on 2010-10-19
Hi,
I start apache (apachectl start) at  11:26 and i see 4 process apache. Then after one hour i see other apache process started: at 11:35, 11:38, 11:43, 12:00

who started those apache?????? 


root     26483     1  0 11:26 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26484 26483  0 11:26 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26490 26483  0 11:26 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26491 26483  0 11:26 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26585 26483  0 11:35 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26626 26483  0 11:38 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26676 26483  0 11:43 ?        00:00:00 /apache/apache2/bin/httpd -k start
nobody   26829 26483  0 12:00 ?        00:00:00 /apache/apache2/bin/httpd -k start



thanks for all.

---

### Post by Barriehie on 2010-10-19
Apache starts them:
[http://httpd.apache.org/docs/2.0/mod/worker.html](http://httpd.apache.org/docs/2.0/mod/worker.html)

---

### Post by issamneo on 2010-10-19
Thank you.

---

