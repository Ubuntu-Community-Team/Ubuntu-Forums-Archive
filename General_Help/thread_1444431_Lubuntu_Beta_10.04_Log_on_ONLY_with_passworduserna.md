---
title: "Lubuntu Beta 10.04: Log on ONLY with password/username"
date: 2010-04-01
forum: General Help
---

### Post by Pott on 2010-04-01
I installed with auto login, but it still asks me my username + password every time I log in. 
The option to change this under Users and Groups is greyed out.

Anyone know why that is or if there's a way around..?

Thanks!
EDIT: I think I found out why:

on the log in menu I still have access to several desktops: standard Lubuntu, Lubuntu netbook, pure Openbox, KDE/openbox (not working) and Gnome/openbox (not working either)

So I guess until I figure out how to get rid of all of these I'll always need to log in... which is a bit of a bummer but then again it's very quick to boot.

---

### Post by vzomik on 2010-04-01
sudo vi /etc/gdm/custom.conf

---

### Post by Pott on 2010-04-01
Thanks! I'll give this a try with Leafpad (standard editor with Lubuntu)!

EDIT: well it IS set as autologin = true, so that wasn't it. But I edited /etc/lxdm/default.conf and /etc/lxdm/lxdm.conf and all is well now :)

---

