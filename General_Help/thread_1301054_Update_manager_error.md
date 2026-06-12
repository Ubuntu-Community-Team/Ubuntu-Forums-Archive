---
title: "Update manager error"
date: 2009-10-25
forum: General Help
---

### Post by bobdabilda on 2009-10-25
'E:Type \u2018view\u2019 is not known on line 57 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Does anyone know how to fix this

---

### Post by P4man on 2009-10-25
looks like you accidentally pasted something in your sources list :)

Just run
```

gksu gedit /etc/apt/sources.list
```

and delete the offending line. It should stand out, but if in doubt, post the contents here.

---

### Post by bobdabilda on 2009-10-25
Thanks for that just so simple

---

### Post by vinutux on 2009-10-25
plz...mark thread SOLVED

---

