---
title: "Output of gnome terminal"
date: 2006-05-02
forum: General Help
---

### Post by SreckoMicic on 2006-05-02
Where are saved outputs of terminal? I'm compiling something and when error is shown it is pretty long so I can't saw it's beginning.

---

### Post by frodon on 2006-05-02
Launch your make command like that : ```
make >& debug.txt
```The characters **>&** allow to send all the terminal output (including errors) in the following file (here debug.txt).
So launch your make command like that then open the file debug.txt to see what happened.

Good luck ;)

---

### Post by SreckoMicic on 2006-05-02
Tnx a lot with this FAST answer.

---

