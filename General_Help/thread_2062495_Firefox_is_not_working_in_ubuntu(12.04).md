---
title: "Firefox is not working in ubuntu(12.04)"
date: 2012-09-25
forum: General Help
---

### Post by isha9 on 2012-09-25
Hi,


I am using ubuntu12.04, but my firefox is not working.


isha@loclhost:firefox
X_PCOMGlueload error for file /usr/lib/firefox/libxpcom.so
Xibxulso: connot open shared object file:
No such fire or directory.

Any help would be apperciate.


Isha

---

### Post by TenPlus1 on 2012-09-25
Try re-installing Firefox to see if that helps, go into Terminal and type these commands:

mv ~/.mozilla ~/mozilla-backup

sudo apt-get purge firefox firefox-globalmenu firefox-gnome-support

sudo apt-get install firefox firefox-globalmenu firefox-gnome-support

---

### Post by isha9 on 2012-09-25
Thanks for reply, but  apt-get also is not working,because recently i upgraded my gcc version , after that my ubuntu screen became blank and nothig to work.this is my problem,kindly any solutions?




Thanks,
Isha.

---

### Post by vasa1 on 2012-09-25
[http://askubuntu.com/questions/192694/firefox-is-not-working](http://askubuntu.com/questions/192694/firefox-is-not-working)

---

