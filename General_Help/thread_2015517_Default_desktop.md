---
title: "Default desktop"
date: 2012-07-03
forum: General Help
---

### Post by rickm1945 on 2012-07-03
I installed Cinnamon 1.4 and used it for a time and when I logged back in I wanted the standard Ubuntu 12.04 desktop. Is the default Ubuntu 2D or Ubuntu?

---

### Post by deadflowr on 2012-07-03
The default is Ubuntu, however upon boot a command runs to see if your system is up to snuff, and able to run full unity, if not it automatically loads unity2d.

You can check your systems ability from the command line with

```
/usr/lib/nux/unity_support_test -p
```

If any of the answers come back no, then full unity will not load.

---

### Post by sudodus on 2012-07-03
> **rickm1945 said:**
> I installed Cinnamon 1.4 and used it for a time and when I logged back in I wanted the standard Ubuntu 12.04 desktop. Is the default Ubuntu 2D or Ubuntu?
As far as I understand it is Ubuntu (meaning Unity, not Unity 2d).

Select Unity 2d or some light gnome-session or fall-back to make it work better with middle-aged hardware. (You need Xubuntu or Lubuntu or something else (e.g. Cinnamon) to make it work better with old hardware.)

---

### Post by rickm1945 on 2012-07-03
> **deadflowr said:**
> The default is Ubuntu, however upon boot a command runs to see if your system is up to snuff, and able to run full unity, if not it automatically loads unity2d.

You can check your systems ability from the command line with

```
/usr/lib/nux/unity_support_test -p
```If any of the answers come back no, then full unity will not load.
Thanks I had all yes

---

