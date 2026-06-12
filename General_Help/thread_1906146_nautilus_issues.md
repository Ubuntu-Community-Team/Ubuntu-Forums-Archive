---
title: "nautilus issues"
date: 2012-01-08
forum: General Help
---

### Post by bluexrider on 2012-01-08
Running 11.04
Have nautilus elementary 2.32.2 installed. Has been working fine 

lost the slider (lower right corner) and function F4

F7 works   

How can I reset the defaults

---

### Post by bluexrider on 2012-01-08
```
gconf-editor
```apps/nautilus/preferences

show_clutter 'yes'
clutter_test '0'

enabled statusbar

---

