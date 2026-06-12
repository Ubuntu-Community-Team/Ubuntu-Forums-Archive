---
title: "How to sandbox programs that you compile yourself?"
date: 2012-05-31
forum: General Help
---

### Post by asuastrophysics on 2012-05-31
Hi,

Does anyone know if there is a way to "shield" ubuntu from any programs that you compile yourself? If I compile program A while program A is already installed via the repositories, Ubuntu will try to use the compiled version by default automatically. How do you stop this? In other words, how do I "sandbox" my compiled programs?

For example,

I tried to compile a version of unity. However, unity was already installed via the repositories. During the build, "make" failed. Ubuntu went ahead and tried to use my compiled version of unity as default anyway, which resulted in me having no window manager

---

### Post by asuastrophysics on 2012-06-03
bump

---

### Post by wilee-nilee on 2012-06-03
> **asuastrophysics said:**
> bump

Use a virtual to do your tinkering, Dr. Frankenstein. ;)

---

### Post by Gyokuro on 2012-06-03
Hi

Own applications should be placed in /usr/local/bin ... or ~/bin or /opt - that's a good practice so that distribution applications get not messed up with self compiled apps.

---

