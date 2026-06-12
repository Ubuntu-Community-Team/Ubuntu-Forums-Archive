---
title: "Can Open Packages"
date: 2009-12-13
forum: General Help
---

### Post by AngelAir on 2009-12-13
I have tried to installed the Lightscribe System Software but when it tries to open the DEB package an error statement comes up that says:

/tmp/lightscribe-1.18.10.2-linux-2.6-intel.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I tried the RPM package but I receive the same error.

If I open any other DEB package; they work.

Does someone has any idea or experience with  this Lightscribe app that can help me. T.I.A

---

### Post by 3rdalbum on 2009-12-13
Are you absolutely sure that your download worked correctly?

Try:

```
sudo dpkg -i /tmp/lightscribe-1.18.10.2-linux-2.6-intel.deb
```

which is the manual method of installation.

---

### Post by Leppie on 2009-12-13
what's the output of:
```
$which gdebi
```
if it gives you something like:
```
/usr/bin/gdebi

```
you can open a filemanager (like nautilus or thunar) right click a .deb package and select "Open With GDebi Package Installer" or "Open With Other Application..." and then select GDebi or click "Use a custom command:" and type gdebi in the input box that appears, then click "Open"

---

