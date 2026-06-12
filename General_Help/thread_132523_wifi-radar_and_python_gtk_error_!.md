---
title: "wifi-radar and python gtk error !?"
date: 2006-02-18
forum: General Help
---

### Post by Lightmans on 2006-02-18
Hello my friends,
can somebody help me with this error...

i installed it with apt-get install wifi-radar and now i can´t start it... 
i need the tool to scan my network with my wlan0 :(

is sombody out there who now somethong about this error?

```
root@lightmans:/home/harald# wifi-radar
Traceback (most recent call last):
File "/usr/sbin/wifi-radar", line 1798, in ?
import gtk, gobject
File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode
root@lightmans:/home/harald# 
```

greets,
Lightmans

---

