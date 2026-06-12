---
title: "how to get back the default top panel"
date: 2010-01-29
forum: General Help
---

### Post by ze_49 on 2010-01-29
i accidentally remove my top panel...how do i get the default panel back?

---

### Post by junapp on 2010-01-29
from:[http://ubuntuforums.org/archive/index.php/t-392387.html](http://ubuntuforums.org/archive/index.php/t-392387.html)
not sure if still applicable

```

gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

---

### Post by r_s on 2010-01-29
even if you remove the .gnome directory , you will be able to revert back to the original settings.

---

### Post by ze_49 on 2010-01-29
i 'll try

---

### Post by junapp on 2010-01-29
another post of interest which may help:
[http://ubuntuforums.org/showthread.php?t=812972&highlight=lost+gnome-panel](http://ubuntuforums.org/showthread.php?t=812972&highlight=lost+gnome-panel)

---

### Post by ze_49 on 2010-01-29
thanks

---

### Post by junapp on 2010-01-29
or more recently:
[http://ubuntuforums.org/showpost.php?p=8731215&postcount=2](http://ubuntuforums.org/showpost.php?p=8731215&postcount=2)

---

