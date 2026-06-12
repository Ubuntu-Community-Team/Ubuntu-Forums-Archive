---
title: "Problem installing package"
date: 2012-04-12
forum: General Help
---

### Post by jroa on 2012-04-12
I am trying to install Virtualbox.  I downloaded from Oracle's website because the Virtualbox in the repositories did not let me run Windows 8.

When I try to install it, I get a message saying Dependency is not satisfiable: libc6 (>= 2.15).

Apparently I need to update libc6 since the one in the repositories is 2.13.

This is the first time I have had to deal with this.  What command do use?  I am using Ubuntu 11.10.

---

### Post by roelforg on 2012-04-12
Fix:
upgrade to ubuntu 11.10
Upgrading only libc isn't worth it, you'd have to do like 95% of the probs as well as everything needs it (static compiles and kernel excluded).
Just upgrade ubuntu and the new libc comes with it.

---

### Post by jroa on 2012-04-12
I am using 11.10.  This is the most recent stable version, isn't it?

---

