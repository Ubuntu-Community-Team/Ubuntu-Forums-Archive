---
title: "Sound converter won't open"
date: 2011-09-30
forum: General Help
---

### Post by Jamho93 on 2011-09-30
I got some kind of a problem here. I try to open sound converter but it won't open. So I tried opening it in the terminal and this popped out 


SoundConverter 1.4.4

(process:18827): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
  using Gstreamer version: 0.10.30, Python binding version: 0.10.19
Traceback (most recent call last):
  File "/usr/bin/soundconverter", line 108, in <module>
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


so what should I do I really want this working!

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-30
Try this:
```
sudo dpkg-reconfigure locales
```

---

### Post by Jamho93 on 2011-09-30
nope. it did a bunch of things but it's still the same. :/

---

### Post by papu40000 on 2012-01-03
> **OpEn_SoUrCe_RoCkS said:**
> Try this:
```
sudo dpkg-reconfigure locales
```

iep! This worked for me!

---

### Post by Arielxgbarton on 2012-01-03
I know this is very un-helpful, but you could try another converter. What format are you trying to convert

---

