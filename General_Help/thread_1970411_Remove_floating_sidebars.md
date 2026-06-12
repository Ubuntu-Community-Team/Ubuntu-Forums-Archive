---
title: "Remove floating sidebars"
date: 2012-05-01
forum: General Help
---

### Post by kabukiM0n0 on 2012-05-01
Hey all.

What is the code to remove the floating sidebars that come standard in Ubuntu 12.04?

Thank you

K.m

---

### Post by 4museman on 2012-05-03
Hi! Do you mean the sidebar, which is default in Unity? You can get rid of it by using original Gnome AFAIK.

---

### Post by ubuntu27 on 2012-05-03
Those sidebars are called "Overlay scrollbar"

and it can be disabled by

```
sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
```

More info at [How To Disable The Overlay Scrollbars In Ubuntu]("http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html")

---

