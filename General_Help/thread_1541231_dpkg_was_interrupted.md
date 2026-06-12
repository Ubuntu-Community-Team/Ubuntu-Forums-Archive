---
title: "dpkg was interrupted"
date: 2010-07-28
forum: General Help
---

### Post by DayLite on 2010-07-28
I just installed Ubuntu 10.04 on my laptop. I cannot install anything without the pop up screen.

E: dpkg was interrupted, you must manually run 'sudo dpkg--configure-a' to correct the problem.

E: cache 7 open () failed, please report

What does that mean?  How do I mannually run?

---

### Post by drs305 on 2010-07-28
Open a terminal: Applications > Accessories > Terminal

Type:```

sudo dpkg --configure -a
```
When it asks for your password, type it in. You will not see it as you type. Press ENTER after typing it.

---

