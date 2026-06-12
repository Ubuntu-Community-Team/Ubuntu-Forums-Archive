---
title: "How to install location path in Nautilus titlebar"
date: 2012-05-25
forum: General Help
---

### Post by Ralph L on 2012-05-25
I recently installed ubuntu 12.04 and am running gnome classic (no effects).  On previous systems the path to the current file/folder was in the Nautilus titlebar.  I think I also saw it once in 12.04, but I can't get it back.  Does anybody know how to enable display of the current Nautilus location in the title bar?

Thank you

---

### Post by matt_symes on 2012-05-25
Hi

Open a terminal and type (or copy and paste)

```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

Change true to false to reset back.

Kind regards

---

### Post by sgage on 2012-05-25
> **matt_symes said:**
> Hi

Open a terminal and type (or copy and paste)

```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

Change true to false to reset back.

Kind regards

And to just get the path on the fly, Ctl-L will toggle from breadcrumb to full text path.

---

