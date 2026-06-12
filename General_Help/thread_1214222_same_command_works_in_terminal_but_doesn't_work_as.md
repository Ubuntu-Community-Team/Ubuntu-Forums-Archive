---
title: "same command works in terminal but doesn't work as a launcher"
date: 2009-07-15
forum: General Help
---

### Post by chriskin on 2009-07-15
titles says it all, can you tell me why this might be happening?

the command is ```
metacity --replace & /home/christos/Music/UrbanTerror/ioUrbanTerror.x86_64 && compiz --replace
``` and works fine through terminal or through a script, but when i make a launcher out of it metacity replaces but it stops there

---

### Post by michy99 on 2009-07-15
Try using && instead of &```
metacity --replace && /home/christos/Music/UrbanTerror/ioUrbanTerror.x86_64 && compiz --replace
```

---

### Post by chriskin on 2009-07-15
i thought it , but wouldn't that cause the command to stop half way even while in terminal?

---

### Post by chriskin on 2009-07-15
just tried it, it didn't work :S

---

### Post by michy99 on 2009-07-15
If the first command executes successfully, the second one should then execute.

---

### Post by chriskin on 2009-07-15
strangely enough though, it executes the first command perfectly while in terminal , but it doesn't through the launcher. do they work differently?

---

### Post by t4thfavor on 2009-07-15
Long shot, but when you replace the window manager would that then stop any launchers that window manager had, or is this way off base.

Kinda like (tell my wm to launch a window, right after that I replace the wm with a new one that I never told to open a window)

---

### Post by michy99 on 2009-07-15
Maybe you need to give the whole path to metacity (/usr/bin/metacity)

---

### Post by chriskin on 2009-07-15
i just made a script of it and placed it on the desktop

it really isn't worth spending your time on it, i thought someone would already know the answer
thanks :)

---

### Post by t4thfavor on 2009-07-15
Good idea, its kinda a niche market to want to run all of those commands in that order. Sorry we couldn't help more.

---

### Post by chriskin on 2009-07-15
the command run very nicely in that order, it's the launcher thing that doesn't

but it isn't needed so ok :)

---

