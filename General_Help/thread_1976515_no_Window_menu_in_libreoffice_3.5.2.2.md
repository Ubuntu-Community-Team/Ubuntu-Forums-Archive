---
title: "no Window menu in libreoffice 3.5.2.2"
date: 2012-05-08
forum: General Help
---

### Post by chaopoch on 2012-05-08
I am using Ubuntu 12.04, and no matter in Ubuntu(unity) session or gnome classic session, I can not find **[COLOR="Red"]Window[/COLOR]** dropdown menu in global menu to freeze rows or columns as headers in libreoffice 3.5.2.2.

Will that be caused by global menu? any way to fix it? 
Thanks for reply.

---

### Post by vasa1 on 2012-05-08
> **chaopoch said:**
> I am using Ubuntu 12.04, and no matter in Ubuntu(unity) session or gnome classic session, I can not find **[COLOR="Red"]Window[/COLOR]** dropdown menu in global menu to freeze rows or columns as headers in libreoffice 3.5.2.2.

Will that be caused by global menu? any way to fix it? 
Thanks for reply.

I'm pretty convinced it **is** due to the global menu in the form of lo-menubar. It does interfere with the genuine LibreOffice menu and also with some keyboard short cuts. It really isn't ready for prime time, IMO. There are bugs filed in Launchpad but I can't give you the links right now.

---

### Post by vasa1 on 2012-05-08
Here are a couple:
[https://bugs.launchpad.net/lo-menubar/+bug/760879](https://bugs.launchpad.net/lo-menubar/+bug/760879)
and
[https://bugs.launchpad.net/ubuntu/+source/lo-menubar/+bug/739184](https://bugs.launchpad.net/ubuntu/+source/lo-menubar/+bug/739184)

And if you want to get rid of lo-menubar, it wasn't possible via the extensions manager built-in to LibreOffice the last time I looked. You need to use **sudo apt-get purge** from the terminal while LibreOffice isn't running (just to be safe).

---

