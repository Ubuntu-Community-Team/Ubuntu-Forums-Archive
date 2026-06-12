---
title: "pipe history into vim"
date: 2010-09-16
forum: General Help
---

### Post by l3ecl on 2010-09-16
when i display the history of my commands i pipe it unto less:

history | less

what if instead of less, i want the output unto vim?

ps: is there a way to copy the commands from "history | less" without using the mouse? maybe like: line number + y (ie 7y) copies command  number 7 from history into the buffer.

---

### Post by SlugSlug on 2010-09-16
```
history >list
```
```
vi list
```

---

