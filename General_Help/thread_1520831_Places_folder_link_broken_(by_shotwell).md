---
title: "Places folder link broken (by shotwell?)"
date: 2010-06-30
forum: General Help
---

### Post by sebastianrimbaud on 2010-06-30
I'm not sure what happened, but lately whenever I click any of the folder shortcuts to "Documents" "Pictures" "Home" etc instead of taking me to the folder, it will open up shotwell.

Uninstalling shotwell, fixes the problem. But I was wondering if there was a different way to fix the issue. I've grown to like shotwell and would hate to change.

Is there a way to figure out how to fix the problem?

---

### Post by schop on 2010-10-22
I'm having the exact same problem. Clicking any link in the 'Places' menu will open Shotwell instead.

Any help would be appreciated, this is _very_ annoying

---

### Post by sikander3786 on 2010-10-22
From Terminal, type

```
nautilus
```

Right click any folder listed, Open with other application > File Browser > Remember this application for 'folder' files.

---

### Post by schop on 2010-10-22
> **sikander3786 said:**
> From Terminal, type

```
nautilus
```

Right click any folder listed, Open with other application > File Browser > Remember this application for 'folder' files.

So obvious...thanks!

---

### Post by DuncanNZ on 2010-11-11
> **sikander3786 said:**
> Right click any folder listed, Open with other application > File Browser > Remember this application for 'folder' files.

I had the same problem, wonder how it happens? I went looking for an entry called 'Nautilus' in the applications list... didn't get far that way. Thanks

---

### Post by billrandle on 2010-12-03
Yes....this works! Thanks
Code:
nautilus
Right click any folder listed, Open with other application > File Browser > Remember this application for 'folder' files.

---

### Post by daklein on 2011-01-03
Yes, this still fixes it.  on an updated 10.10 system,  after using shotwell it must have started using shotwell to open any folder links?    Thanks

---

### Post by sut100 on 2011-01-19
Just found this,I'm a new user & I had the same problem......Fixed it from your directions,Thank you very much.

---

### Post by hicaspdx on 2011-10-18
I dont have the option to "remember" all i get is remove open or cancel

---

