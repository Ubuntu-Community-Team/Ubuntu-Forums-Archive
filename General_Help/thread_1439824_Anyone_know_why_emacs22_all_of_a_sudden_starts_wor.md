---
title: "Anyone know why emacs22 all of a sudden starts working?"
date: 2010-03-26
forum: General Help
---

### Post by Ubu4moi on 2010-03-26
I'm running Ultimate Edition 2.0 64bit. Sometimes emacs22 starts running on nthe background taking 90+% of the resources for a reason I don't know. It runs for a few minutes and then shuts down by itself then other processes like mandb also run and turn off. Can anyone explain what's going on?

---

### Post by jtappin on 2010-03-26
System cron jobs. 

The mandb is clearly the system keeping the man pages database up to date. The emacs less obvious but probably checking and compiling any changed lisp files.

---

