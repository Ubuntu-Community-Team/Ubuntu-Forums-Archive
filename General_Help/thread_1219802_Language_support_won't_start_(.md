---
title: "Language support won't start :("
date: 2009-07-22
forum: General Help
---

### Post by renbla on 2009-07-22
I go to system>admin>language support ~~~~>nothing happen :(:(. The time i installed ubuntu, it ran smoothly, but after playing around, i got that :confused:. Any ideas how to fix this??

---

### Post by jerrrys on 2009-07-22
try "fix broken packages" or just "reinstall" in SynapticPackageManager

---

### Post by renbla on 2009-07-22
Srr i don't know the package's name in synaptic :P

---

### Post by michy99 on 2009-07-22
If you start it from the terminal with this command:```
gnome-language-selector
```do you get any error messages?

---

### Post by jerrrys on 2009-07-22
Synaptic>Edit>Fix broken packages...just click on it, you may get lucky

---

### Post by renbla on 2009-07-23
> **michy99 said:**
> If you start it from the terminal with this command:```
gnome-language-selector
```do you get any error messages?

I got this and i don't know what in the world it's talking a bout :( 
```
gnome-language-selector
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 13, in <module>
    from LanguageSelector.gtk.GtkLanguageSelector import GtkLanguageSelector
ImportError: No module named LanguageSelector.gtk.GtkLanguageSelector
```

---

