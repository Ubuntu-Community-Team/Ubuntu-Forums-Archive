---
title: "Cannont resolve host Sebain-Wolf"
date: 2009-09-25
forum: General Help
---

### Post by Sethun on 2009-09-25
So when I attempt to do gedit and a few other terminal things I get Cannot resolve host Sebain-Wolf and I also get (gedit:30194): Gtk-WARNING **: cannot open display: :0.0
I'm guessing it has something to do with me recently changing my hostname

---

### Post by fooman on 2009-09-25
open a terminal and run this command:

```
cat /etc/hosts
```

...post the output back here.

---

### Post by fooman on 2009-09-25
see here how to fix:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

hope it helps.

---

### Post by Sethun on 2009-09-25
I can't actually run cat /ect/hosts it would give me directory doesn't exist or something along those lines. But when I did a restart my hostname reset back to original...

---

