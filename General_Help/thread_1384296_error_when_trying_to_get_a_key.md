---
title: "error when trying to get a key"
date: 2010-01-18
forum: General Help
---

### Post by hyburn on 2010-01-18
hey folks,

im trying to get my virtualbox to work, so I can properly update,

wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -


gives me an error of:

gpg: no valid OpenPGP data found.

---

### Post by Kobalt on 2010-01-18
Try to click on the link, save the text key into a text file. Then run Administration > Sysytem > Software sources. In the Authentification area you can import a local key, point it to your text file. 
This should work.

---

### Post by hyburn on 2010-01-18
WOW cobalt I love you man thanks so much its not screwing up

---

### Post by Kobalt on 2010-01-18
You're welcome :)

---

