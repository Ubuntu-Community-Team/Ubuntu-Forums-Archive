---
title: "kwallet and wireless password"
date: 2012-07-22
forum: General Help
---

### Post by icegood on 2012-07-22
Why wireless connection asks for pwd irrespectivetly that kwallet pwd was inputted before or not? How to see whetherkwallet REALLY cache wireless pwd?

---

### Post by zandisini on 2013-01-01
It's because KDE desktop by default encrypt your wireless password in kwallet. There are a way to bypass the kwallet password prompting for wifi.

1. Right click network applet, select network manager setting
2. Select other
3. Change the "store connection secrects" from "in secure storage to" to "in file (unencrypted)"
4. Select OK

Keep in mind that with this, your wifi password isn't encrypted

---

