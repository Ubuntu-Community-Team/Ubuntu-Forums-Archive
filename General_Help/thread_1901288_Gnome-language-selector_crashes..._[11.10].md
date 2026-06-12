---
title: "Gnome-language-selector crashes... [11.10]"
date: 2011-12-28
forum: General Help
---

### Post by LittleJakub on 2011-12-28
```
kuba@GLaDOS:~$ sudo gnome-language-selector
[sudo] password for kuba: 

(gnome-language-selector:5500): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(gnome-language-selector:5500): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(gnome-language-selector:5500): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(gnome-language-selector:5500): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(gnome-language-selector:5500): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(gnome-language-selector:5500): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 27, in <module>
    options=options)
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 192, in __init__
    self.updateLocaleChooserCombo()
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 57, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 853, in updateLocaleChooserCombo
    self.updateExampleBox()
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 926, in updateExampleBox
    locale.setlocale(locale.LC_ALL, mylocale)
  File "/usr/lib/python2.7/locale.py", line 539, in setlocale
    locale = normalize(_build_localename(locale))
  File "/usr/lib/python2.7/locale.py", line 447, in _build_localename
    language, encoding = localetuple
ValueError: too many values to unpack

```

Whenever I try to start the app, it crashes... I give the output of trying to run it from terminal. I hope we can find a way to make it work! :)

---

