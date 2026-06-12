---
title: "Separate x monitor on 10.04"
date: 2010-06-30
forum: General Help
---

### Post by NikitaUtiu on 2010-06-30
Hi, all!
I am using Lucid and nvidia x server. I have just installed a new x screen on my dual monitor (p.s. the tv).
I have 2 questions:
1) Why doesn't my nvidia x settings save the overscan compensation ?
2) Is there any way I can center the image on the screen and stretch it from the settings (my tv doesn't have  auto center)?

---

### Post by fooman on 2010-06-30
to save the settings,  you need to run nvidia-settings as root.

open a terminal and type or copy/paste the following:

```
gksudo nvidia-settings
```

make the changes,  click apply,  then click "save to x configuration file".

---

### Post by NikitaUtiu on 2010-07-01
> **fooman said:**
> to save the settings,  you need to run nvidia-settings as root.

open a terminal and type or copy/paste the following:

```
gksudo nvidia-settings
```make the changes,  click apply,  then click "save to x configuration file".

I've already tried this, but it doesn't save the overscan compensation.

---

### Post by NikitaUtiu on 2010-07-02
Anyway. Thanks!

---

