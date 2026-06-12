---
title: "how do get the id of a specific window? (shellscript)"
date: 2009-11-15
forum: General Help
---

### Post by skaldyr on 2009-11-15
How could i get the window id of the firefox window?

I have tried xwininfo but i cant seem to get it to do what i want. i can only get the id by using the cursor.

---

### Post by Matt__ on 2009-11-15
you mean something like 
```
top
```
to list all open processes/IDs/mem use/uptime

---

### Post by skaldyr on 2009-11-15
I need the window id not the process id.

but thanks for replying

---

### Post by skaldyr on 2009-11-15
i think i found a way in the xwininfo man pages

```
xwininfo -name  "name of window" 
```

---

