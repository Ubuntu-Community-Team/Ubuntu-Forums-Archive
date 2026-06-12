---
title: "I get this weird error when I use sudo in terminal"
date: 2009-10-17
forum: General Help
---

### Post by lavadisco on 2009-10-17
```
Xlib:  extension "RANDR" missing on display ":0.0".
```

Doesn't prevent me from doing what I want, but perhaps I should fix whatever is causing it? Anybody know why this is happening?

---

### Post by eric3_14159 on 2009-11-09
It sounds like logging in as root is trying to trigger some program which expects it to have its own X11 session. Try checking /root/.bashrc and /root/.bash_profile and looking for programs which may be trying to run or environment variables being set.

---

### Post by catco_designs on 2009-11-09
are you also getting alot of xsession errors?
do you receive the message everytime or just at random?
Does it cause any issue besides printed message?

---

