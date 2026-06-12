---
title: "gnome-app-install"
date: 2006-03-26
forum: General Help
---

### Post by nahas on 2006-03-26
i am not able to run  gnome-app-install,the error is given below..pls help

gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

---

### Post by arnieboy on 2006-03-26
[QUOTE=nahas]i am not able to run  gnome-app-install,the error is given below..pls help

gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory[/QUOTE]
the missing file is in the firefox package.
reinstall firefox from synaptic.

---

### Post by nahas on 2006-03-26
[QUOTE=arnieboy]the missing file is in the firefox package.
reinstall firefox from synaptic.[/QUOTE]
tnx arnie......

---

