---
title: "Hide A Window?"
date: 2009-11-19
forum: General Help
---

### Post by MikeVaughanG on 2009-11-19
I'm running 9.10

Im using a program in Terminal that I need to keep running (TwitNotify.py)

And the window gets in the way. 

Is there a way to hide just one window?

---

### Post by cariboo on 2009-11-19
Move it to another workspace?

---

### Post by loell on 2009-11-19
prolly create a launcher?

---

### Post by MikeVaughanG on 2009-11-20
> **loell said:**
> prolly create a launcher?

Creating A Launcher worked well. 

Thanks.

---

### Post by P4man on 2009-11-20
If you ever again need to launch an app from a terminal and want to "detach" it from the terminal (so you can close the terminal without killing the app) simply add
```
& disown
```
after the command.

---

