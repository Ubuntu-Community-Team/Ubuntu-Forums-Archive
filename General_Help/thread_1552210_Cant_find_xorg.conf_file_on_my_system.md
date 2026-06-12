---
title: "Cant find xorg.conf file on my system"
date: 2010-08-13
forum: General Help
---

### Post by BrianG007 on 2010-08-13
Hi, I am new to linux and I have Ubuntu 10.4 installed on my system. I am trying to get a touchscreen driver installed and I am talking to the techs at the company and they asked for a copy of my xorg.conf file. I have done several searches on my computer and looked on other forums posts as to where that file should be located and I cannot find this file anywhere on the system. Does Ubuntu 10.4 even have a xorg.conf file? Any suggestions/responses would be appreciated. Thanks!

---

### Post by earthpigg on 2010-08-13
hi,

just to make sure, what does this return?

```
cat /etc/X11/xorg.conf
```

and this,

```
ls /etc/X11
```

---

### Post by Noz3001 on 2010-08-13
Ubuntu doesn't have one by default. If you do have one for some reason, it would be located in /etc/X11/

---

