---
title: "missing window controls"
date: 2011-05-22
forum: General Help
---

### Post by kree8or on 2011-05-22
Hi ,
since upgrading to 11.04 i'm missing "the windows" controls ie the "minimize and maximise" controls.
Where did they go?

---

### Post by kd7swh on 2011-05-22
It sounds like you need to restart your window manager.

I don't know a lot about KDE but running something like:

kde-window-manager --replace 

should do the trick...



In Gnome:

```
 metacity --replace 
```

---

