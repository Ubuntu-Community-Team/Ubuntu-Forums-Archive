---
title: "how do I get rid of extra garbage bin from desktop"
date: 2009-07-02
forum: General Help
---

### Post by charonred on 2009-07-02
I've got a garbage bin in the bottom panel,but I've also got another on the desktop, but I cant' find any way to remove the extra one.

I can't drag it into the other bin (into itself as such), and there is no right click option to delete it.

How do I dump the extra garbage bin ?

---

### Post by -kg- on 2009-07-02
Can you open Nautilus and drag it from the "desktop" directory to another directory?  That way, it would be "out of sight; out of mind."

And you might even be able to delete it from another directory.  You might need to launch Nautilus using:

```
gksu nautilus
```

which would give Nautilus root permission for the operation.

---

### Post by Elfy on 2009-07-02
Alt+F2 - run gconf-editor

Navigate to apps/nautilus/desktop - uncheck the trash_icon_visible key

---

### Post by charonred on 2009-07-02
thanks
I've made a note of that > alt+F2 run gconf-editor
apps/nautilus/desktop - uncheck the trash_icon_visible key 

very useful I suspect.

---

