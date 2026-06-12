---
title: "Empathy problems on ubuntu 9.10 upgrade"
date: 2009-10-30
forum: General Help
---

### Post by r4z0rw0lf on 2009-10-30
Okay, after a whole night of upgrading, I finally got Ubuntu 9.10,
I tried to start empathy but kept getting errors like:
```

empathy: error while loading shared libraries: libicui18n.so.38: cannot open shared object file: No such file or directory

```
so i created a symblic link to the libs, but now i am getting this error:
```
empathy: symbol lookup error: /usr/local/lib/libwebkit-1.0.so.2: undefined symbol: UCNV_FROM_U_CALLBACK_SUBSTITUTE_3_8

```
i need help with this because i REALLy wanted to try empathy!:D

---

### Post by r4z0rw0lf on 2009-10-30
bump

---

### Post by claymater on 2009-10-30
Personally I like pidgin more (Tab switching doesnt work *well* in empathy) But you can try to reinstall it (software center).

---

### Post by r4z0rw0lf on 2009-10-30
software manager gives this: 
```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
ImportError: libicui18n.so.38: cannot open shared object file: No such file or directory

```
so it appears to want libicu18, but thats not in my repos

---

### Post by r4z0rw0lf on 2009-10-31
bump?

---

### Post by r4z0rw0lf on 2009-10-31
okay, i did a fresh install, Empathy is working now.marking as solved

---

