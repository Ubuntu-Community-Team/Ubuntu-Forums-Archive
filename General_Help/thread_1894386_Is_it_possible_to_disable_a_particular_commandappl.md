---
title: "Is it possible to disable a particular command/application?"
date: 2011-12-12
forum: General Help
---

### Post by arroy_0209 on 2011-12-12
Is it possible to disable a particular command or application (e.g., rhythmbox) in ubuntu 10.04LTS? In case it is possible, please explain the procedure. In case I want to enable the command/application later, how do I do that?

---

### Post by scottbomb on 2011-12-12
I believe chmod would work for this. Google chmod ubuntu as there are tutorials on it, perhaps this one: 
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

Goes something like this:

sudo chmod a-x name_of_application

---

### Post by devansh.j2007 on 2011-12-12
Disabling as scottbomb said is 

```
sudo chmod ugo-x /usr/bin/rhythmbox
```

whilw enabling it again is

```
sudo chmod ugo+x /usr/bin/rhythmbox
```


well i wonder if it workswithout /usr/bin/ ............

---

### Post by deserthowler on 2011-12-12
> **arroy_0209 said:**
> Is it possible to disable a particular command or application (e.g., rhythmbox) in ubuntu 10.04LTS? In case it is possible, please explain the procedure. In case I want to enable the command/application later, how do I do that?

by disable, do you mean remove it from the menu?

Earl

---

### Post by arroy_0209 on 2011-12-14
Thanks. Chmod really solves my problem.

To deserthowler: I meant an way to stop execution of the program even when typed in the terminal. It need not lead to removing from any particular menu.

---

