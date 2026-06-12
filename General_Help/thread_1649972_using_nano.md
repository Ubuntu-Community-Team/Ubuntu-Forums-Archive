---
title: "using nano"
date: 2010-12-20
forum: General Help
---

### Post by wrixis on 2010-12-20
I was trying to learn and use nano but I can't use the meta shortcuts. For instance, when I want to go to the end of a document (M-/), I enable or disable the mouse. I'm using alt as meta key.

---

### Post by rburkartjo on 2010-12-20
wri does link help

[http://www.nano-editor.org/dist/v1.2/nano.html](http://www.nano-editor.org/dist/v1.2/nano.html)

---

### Post by wrixis on 2010-12-21
I went to that page before to ask here. It says I can use ESC and then the key or alt plus the key but it doesn't work for me.

---

### Post by wrixis on 2010-12-24
up

---

### Post by happyhamster on 2010-12-24
Alt /, Escape / or Escape ? are working fine for me. One thing to investigate is if you have a .nano_history file in your home folder. In a terminal, run:
```

ls -l $HOME/.nano_history

```
to see if it exists. If so, it will likely be owned by root. In that case, change its owner to the desired user instead:
```

sudo chown user:user $HOME/.nano_history

```
Where "user" should be your actual user name. Good luck.

---

### Post by wrixis on 2010-12-24
it doesn't exists :(

---

### Post by wrixis on 2010-12-27
more info: I use Spanish keyboard.

---

