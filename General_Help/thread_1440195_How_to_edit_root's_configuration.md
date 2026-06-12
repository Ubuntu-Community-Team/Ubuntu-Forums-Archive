---
title: "How to edit root's configuration"
date: 2010-03-27
forum: General Help
---

### Post by wirate on 2010-03-27
When I run "sudo systemsettings", it opens my own configuration rather than root's and "kdesu systemsettings" says command not found.

I want to change the appearance of applications I run with kdesu.

---

### Post by sisco311 on 2010-03-27
Try **kdesudo** or **sudo -i** (i.e. sudo -i systemsettings).

EDIT:

Yep. just tested it, both:
```
kdesudo systemsettings
```
and
```
sudo -i systemsettings
```works.

---

### Post by Chame_Wizard on 2010-03-27
```
sudo su 
```

---

### Post by wirate on 2010-03-29
thanks

---

### Post by sisco311 on 2010-03-29
> **wirate said:**
> thanks

You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

