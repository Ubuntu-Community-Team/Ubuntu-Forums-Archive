---
title: "Flash plugin no sound"
date: 2006-06-19
forum: General Help
---

### Post by dentaku65 on 2006-06-19
I have a problem with flash plugin on Firefox, the issue is that the no sound came out during any flash movie on theweb (eg. even all the video@google); I don't think is a problem of Firefox but I suspect is a problem by Dapper, because even with Opera the animation is displayed but without sound.

I've tried many fixes found here to fix this problem (install directly from macromedia file, /tmp/.esd, alsa-oss and more) but still I'm not able to heard sound from flash movies

:confused: 

Anyone have some hints?
TIA

---

### Post by Winblowz on 2006-06-19
Have you tried this?- [https://wiki.ubuntu.com/RestrictedFormats#head-be26b24fedce5b1b8a03c81f4aade9d44543e22e](https://wiki.ubuntu.com/RestrictedFormats#head-be26b24fedce5b1b8a03c81f4aade9d44543e22e)

---

### Post by Rui Pais on 2006-06-19
hi, 
the above link is to install flash. 

Maybe trying [this.]("http://ubuntuforums.org/showthread.php?t=199289")

---

### Post by dentaku65 on 2006-06-19
[QUOTE=Rui Pais]hi, 
the above link is to install flash. 

Maybe trying [this.]("http://ubuntuforums.org/showthread.php?t=199289")[/QUOTE]

This one works, but I have to do:

```
killall esd
```

:rolleyes:

---

### Post by Ramses de Norre on 2006-06-19
You can set esd not to start at login, I think it's in system > sound settings or something like that (I don't use gnome..), you can uncheck start sound server on start up there.

---

