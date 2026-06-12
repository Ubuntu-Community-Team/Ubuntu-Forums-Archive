---
title: "Keyboard layout change"
date: 2012-04-21
forum: General Help
---

### Post by Mactownes on 2012-04-21
So yesterday I installed Ubuntu minimal. When doing the keyboard detection thing, it detected us:international. Now whenever I go to make an apostraphe I have to click it twice. I have tried using the XFCE settings manager to change it, but nothing works.

Does anyone know how to change this?

---

### Post by llamabr on 2012-04-21
What happens if you:

```
setxkbmap us
```

?

---

### Post by Mactownes on 2012-04-21
> **llamabr said:**
> What happens if you:

```
setxkbmap us
```?
Thanks a TON. It worked! One more question: does it persist or will I have to do that every time I log in?

Thanks

---

### Post by llamabr on 2012-04-21
not sure, but if not:

[http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in](http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in)

---

