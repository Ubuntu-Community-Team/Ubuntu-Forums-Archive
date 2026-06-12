---
title: "Change default sound output volume"
date: 2011-06-25
forum: General Help
---

### Post by kanishkdudeja on 2011-06-25
I want to change the default sound output volume to be high than it normally is when the system starts.

How can i change it?

---

### Post by kanishkdudeja on 2011-06-26
bump.

---

### Post by lidex on 2011-06-26
Use alsamixer to set your levels then run this command to save the settings:
```
sudo alsactl store 0
```
Alsamixer is a terminal program accessed by entering it's name in the terminal:
```
alsamixer
```

---

