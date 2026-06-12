---
title: "Need to add progrom to bin list"
date: 2010-01-02
forum: General Help
---

### Post by uclalinux on 2010-01-02
I would like to add a program to the bin list so I may start it by just typing in its name.  The bin file is located under /etc/arduino/

Thanks for the help.

---

### Post by SlugSlug on 2010-01-02
> **uclalinux said:**
> I would like to add a program to the bin list so I may start it by just typing in its name.  The bin file is located under /etc/arduino/

Thanks for the help.


move the executable to /usr/local/bin/

edit:

Depending on what it is or what it needs - it may be best to sym link it

sudo ln -s /etc/ardunin/[filename] /usr/local/bin/

---

### Post by uclalinux on 2010-01-02
The latter was what I was looking for. 

Thanks for the help.

---

