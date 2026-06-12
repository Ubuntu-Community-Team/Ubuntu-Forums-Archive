---
title: "What are exit handlers in linux ?"
date: 2010-05-01
forum: General Help
---

### Post by youralibaba on 2010-05-01
What are exit handlers ? They are piece of code to execute prior to exit() ? plz elaborate.

---

### Post by happyhamster on 2010-05-01
C has the atexit() function which registers functions to be called at (normal) program termination. Other languages may have something similar (python has Py_AtExit() I think).
For example, see:
[http://www.opengroup.org/onlinepubs/009695399/functions/atexit.html](http://www.opengroup.org/onlinepubs/009695399/functions/atexit.html)

---

### Post by youralibaba on 2010-05-01
> **happyhamster said:**
> C has the atexit() function which registers functions to be called at (normal) program termination. Other languages may have something similar (python has Py_AtExit() I think).
For example, see:
[http://www.opengroup.org/onlinepubs/009695399/functions/atexit.html](http://www.opengroup.org/onlinepubs/009695399/functions/atexit.html)


I want to know about exit handler. They are reportedly cal when exit() is made in the c binary code. With them IO cleanup routines are also caled.. and there are thirty two exit handlers.
Plz tell me about these. What do those exit handlers do ?

---

### Post by dino99 on 2010-05-01
> **youralibaba said:**
> What are exit handlers ? They are piece of code to execute prior to exit() ? plz elaborate.

are you programming, if so better to post on programming forum

---

