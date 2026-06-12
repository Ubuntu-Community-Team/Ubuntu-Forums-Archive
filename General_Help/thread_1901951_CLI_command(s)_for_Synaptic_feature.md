---
title: "CLI command(s) for Synaptic feature?"
date: 2011-12-29
forum: General Help
---

### Post by brec on 2011-12-29
Is there a way to use apt-get or another CLI tool instead of a Synaptic window to find the status of a package?  In Synaptic, I type the name of a package and can see whether the system knows of it and if so whether or not it is installed.  Can that kind of query be made from Terminal?

---

### Post by WorMzy on 2011-12-29
Have a look at dpkg-query.

---

### Post by Bonster on 2011-12-29
> aptitude search [package]

the little "i" on the left means it is installed

---

### Post by brec on 2011-12-29
> **Bonster said:**
> the little "i" on the left means it is installed

Ah, yes, I had forgotten that I meant to look into aptitude.  aptitude search implicitly puts a * on either end of the search term rather like synaptic's search box.

---

