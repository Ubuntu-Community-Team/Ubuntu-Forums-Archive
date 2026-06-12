---
title: "[lucid] Disabling the autorun feature!"
date: 2010-07-02
forum: General Help
---

### Post by madmax.santana on 2010-07-02
I have an external WD hard drive on which I have created several partitions to facilitate data arrangement. Whenever I plug it in, all partitions are mounted. That is okay. I want it to automount all partitions. But the annoying thing is all partitions opening and popping up and cluttering my desktop (which I, very dearly, keep very arranged and clean...)

I hate it and want to edit the settings so the folders will not automatically open and pop up into my face...

How would I???

---

### Post by mc4man on 2010-07-02
If it's just the folders auto opening you wish to disable then adjust in File Management -> Media -> bottom of screen - "Browse media when inserted"

File Management is hidden from System -> Preferences menu, many ways - one way in terminal
```
nautilus-file-management-properties
```

Edit: if the icons are also an issue then in terminal
```
gconf-editor
```
apps -> nautilus -> desktop -> disable "volumes_visible"

---

### Post by madmax.santana on 2010-07-02
Thanks!!! That's solved.

---

