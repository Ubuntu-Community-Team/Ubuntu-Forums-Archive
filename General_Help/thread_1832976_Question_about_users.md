---
title: "Question about users"
date: 2011-08-25
forum: General Help
---

### Post by netopalis45 on 2011-08-25
I have noticed that when I use the "who" command it shows that I am logged in twice with the same user account. When using ssh from my laptop, it shows that I am logged in 4 times as if my laptop is logging in twice as well. Is there any explanation for this?

---

### Post by zero2xiii on 2011-08-25
Hay, this is normal.

Not sure about what all the abreviations stand for.. But I do know the TTY one is the base terminal (eg like if you were to use ctrl + alt + F1-6). Its the very base system, loaded at tel init 1 or 2 state I think.. the base of the system.. The other one PTS, I THINK is the graphical interface, xorg, and there should be another one if something is run with 'sudo' or gksudo.

But for every user logged in, there is two "who" outputs. No need to get raised blood preasure over this :D

Cherz

---

### Post by ajgreeny on 2011-08-25
The first line is your user's xsession, and the second line is your user signed on to the Linux session itself;  it is quite normal.  The ssh log-on shows the sdame for your remote session, unless you ssh in to a server with no xsession running, of course.

```
<user>   tty7         2011-08-25 10:56 (:0)
<user>   pts/1        2011-08-25 20:19 (:0.0)
```

---

### Post by zero2xiii on 2011-08-25
> The first line is your user's xsession, and the second line is your user signed on to the Linux session itself; it is quite normal. The ssh log-on shows the sdame for your remote session, unless you ssh in to a server with no xsession running, of course.

+1


Have a look at these threads awell.. Might give some more insight:

[http://ubuntuforums.org/showthread.php?t=833765](http://ubuntuforums.org/showthread.php?t=833765)
[http://ubuntuforums.org/showthread.php?t=814951](http://ubuntuforums.org/showthread.php?t=814951)

They also about this TTY and PTS stuff...

---

