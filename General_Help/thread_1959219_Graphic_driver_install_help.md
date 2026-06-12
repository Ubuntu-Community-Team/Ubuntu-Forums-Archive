---
title: "Graphic driver install help"
date: 2012-04-15
forum: General Help
---

### Post by davidftechman on 2012-04-15
how do i install my driver i have a ati radeon x1250 when i check for drivers it says ther is no properietary driver in use on this system.

---

### Post by kc1di on 2012-04-15
here's a page that may be of help:

[http://askubuntu.com/questions/87395/how-can-i-enable-hardware-acceleration-for-an-ati-radeon-hd]("http://askubuntu.com/questions/87395/how-can-i-enable-hardware-acceleration-for-an-ati-radeon-hd")

---

### Post by Toz on 2012-04-15
ATI has discontinued support for that card, which is why there are no proprietary drivers available. By default, the card will use the open source radeon drivers - which is probably what your using now. You can view the /var/log/Xorg.0.log file to confirm which driver is being loaded.

---

