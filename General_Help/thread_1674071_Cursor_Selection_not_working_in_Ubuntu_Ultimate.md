---
title: "Cursor Selection not working in Ubuntu Ultimate"
date: 2011-01-23
forum: General Help
---

### Post by Tigerlinux on 2011-01-23
Cursor Selection not working in Ubuntu Ultimate,
the pop up windows shown, there are different mouse cursors to choose, but there is no icon to click OK to select it,
Do you face this problem? :(:(:(

---

### Post by Verbeck on 2011-01-23
its an old bug with compiz ( 3+ years). i thought it was fixed in maverick....
the temporary fix is to edit the file* /usr/share/icons/default/index.theme* and specifying the cursor theme there (create the file if it doesn't exist)

*gksu gedit /usr/share/icons/default/index.theme*
```
[icon theme] 
Inherits=CursorThemeName
```and then, re-login

---

### Post by Tigerlinux on 2011-01-23
Thanks, will try it.
In original ubuntu, this problem does not exist.

---

