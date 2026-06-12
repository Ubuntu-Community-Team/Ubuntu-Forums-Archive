---
title: "top bar of all windows missing"
date: 2010-06-02
forum: General Help
---

### Post by kolo-01 on 2010-06-02
hi,
i am unsure how this has happened, but i have somehow removed the top panel with the minimise, maximize and close icons from all of the windows that i open. i can temporarily get them back by restoring metacity in the terminal, but this only works as long as that terminal is running, and i would like to have it back as default, i can also get the bar back by disabling all compiz visual effects in appearance tab, but would like to have both effects and the bar run at the same time. its a bit of an odd problem i know, but if anybody could help me it would be appreciated

---

### Post by lidex on 2010-06-02
Go to CompizConfig Settings Manager -> Effects -> Window Decoration.
Make sure it's enabled and this value is in the 'Command' field:
```
/usr/bin/compiz-decorator
```
Logout/in.

---

### Post by kolo-01 on 2010-06-03
> **lidex said:**
> Go to CompizConfig Settings Manager -> Effects -> Window Decoration.
Make sure it's enabled and this value is in the 'Command' field:
```
/usr/bin/compiz-decorator
```
Logout/in.

thanks a lot, your solution was spot on

---

### Post by lidex on 2010-06-04
Yah! If you would be so kind as to mark the thread as solved using 'thread tools' up top.

---

