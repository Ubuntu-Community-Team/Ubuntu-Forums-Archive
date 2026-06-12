---
title: "How to NOT require login after wake-up"
date: 2010-02-03
forum: General Help
---

### Post by mac666 on 2010-02-03
Hey im on Karmic,
When i hibranate / Sleep my computer i need to login again, since its the computer is "locked".

I have turned on "automatic" loggin et c but that only work if im NOT logged in, but after a wake-up im still logged in and the computer is locked, requiring my action...

Anyone?

---

### Post by anaconda on 2010-02-03
well.. I have Hardy heron, but I suppose it works the same in karmic

open gconf-editor (eg. type (in terminal): gconf-editor)
and go to
/apps/gnome-power-manager/lock
and uncheck the "hibernate" and "suspend" boxes

---

### Post by mac666 on 2010-02-04
Too easy...
Thanks!

---

