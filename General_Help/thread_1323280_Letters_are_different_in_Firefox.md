---
title: "Letters are different in Firefox"
date: 2009-11-11
forum: General Help
---

### Post by Pazau on 2009-11-11
I have a HP dv6645eo with clean install of Ubuntu Linux 9.10.
The letters are as they should be everywhere in the system, apart from Firefox.

[http://img257.imageshack.us/img257/9224/skrmbillede.png](http://img257.imageshack.us/img257/9224/skrmbillede.png)

How do I get normal letters in Firefox?

---

### Post by wrgb2 on 2009-11-11
You can change the font in Firefox from Edit > Preferences > Content Tab.

---

### Post by winotree on 2009-11-11
This changes the anti-aliasing in Firefox.  *According to several users it also changes the font to be uniform system-wide*.  It worked real fine on my device!  :D

sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig

[It may be a good idea to back-up that file first so if it doesn't work the way you thought it should you'll be able to revert to default].

---

### Post by johnboy1313 on 2009-11-11
> **wrgb2 said:**
> You can change the font in Firefox from Edit > Preferences > Content Tab.

if that doesn't work i would try to reinstall the browser

---

### Post by Pazau on 2009-11-11
Whatever I select in the settings, nothing happens.

---

