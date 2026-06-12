---
title: "Strange Mount Problem"
date: 2010-11-09
forum: General Help
---

### Post by MikeyDL on 2010-11-09
I've been using this command to manually mount a windows share to my ubuntu laptop:

```
sudo mount -t cifs //data/bigdocs /home/michael/shares/bdocs -o username='domain.org/myuser',password='password'
```

The whole process works like a champ.  Then we decided to upgrade and get a readynas server with active directory integration.  Now the same command gets me a "permission denied mount error 13" error.

Given that the readynas is a linux box with ACD integration is there anything special I need to do before I can go back to mounting folders on my laptop system?

Anybody have any ideas or tips?

Thanks!

---

