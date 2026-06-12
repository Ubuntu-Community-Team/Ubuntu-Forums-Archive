---
title: "Adding Repositories to sources.list"
date: 2011-10-01
forum: General Help
---

### Post by pstein on 2011-10-01
What is the difference between these two lines (in /etc/apt/sources.list)
 
deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner
 
and
 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
 
Or is it the same?
 
Other question:
 
The entry for a canonical partner Repository is currently commented/disabled in sources.list. When I open now 
 
Applictaion-->Software Center-->Get Software-->Canonical Partners
 
then there are is couple of software listed (eg. Adobe, Skype, UltraEdit,...).
Why does Ubuntu know these software packages if it does not know the underlying Repository?
 
I would have expected at first to add the canonical partner Repository, then to update the source package list and THEN find such software.
 
Peter

---

### Post by dino99 on 2011-10-01
its the good entry:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

then its your choice to activate or comment it, depend on your needs :)

---

### Post by gandaran on 2011-10-01
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
this is the default built in canonical repository 
> deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner
this one looks like it is the same thing but one you have added to software sources
and yes canonical packages show up on software center but if you try to install it'll ask to enable the source first.

---

### Post by foureyesboy on 2011-10-01
@pstein: for your "other question", the other software listed in Software Center but not found in /etc/apt/sources.list.  You can find them under /etc/apt/sources.list.d directory.

---

