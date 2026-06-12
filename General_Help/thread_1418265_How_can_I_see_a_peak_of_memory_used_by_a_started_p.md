---
title: "How can I see a peak of memory used by a started process?"
date: 2010-02-28
forum: General Help
---

### Post by eigenein on 2010-02-28
Ideally, I would like to find something like `time' command:

$ magic_command ./executable
...
memory peak: 100kb

---

### Post by rnerwein on 2010-02-28
hi 
you are looking for a command like "time" -> time is the command you are looking for.
but not the "time is a shell keyword". 
have a look at /usr/bin/time - that's very different. ( man time ).
full function of time you'll get with the "tcsh" - is available with: apt-get install tcsh
hope this help
ciao

---

### Post by eigenein on 2010-02-28
No-no :) That's just example of behaviour I want

---

