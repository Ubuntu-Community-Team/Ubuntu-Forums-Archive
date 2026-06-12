---
title: "Dedicated processor? Set linux to use a processor for a specific program."
date: 2010-08-27
forum: General Help
---

### Post by dragos240 on 2010-08-27
Can I set up my system to use a specific processor to do one task, and another processor for normal applications.

Say for example, I'm using a program that relies heavily on your processor, I have a dual core, so I can use one core for that, and another for normal applications.

Can this be done. If so, how?

---

### Post by davidmohammed on 2010-08-27
Install the "schedtool" package and have a look at the man page for the package - man sched_setscheduler

---

