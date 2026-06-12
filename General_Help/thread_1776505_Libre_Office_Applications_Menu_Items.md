---
title: "Libre Office Applications Menu Items"
date: 2011-06-06
forum: General Help
---

### Post by timgood on 2011-06-06
Following a failed experiment with LibreOffice 3.4 I have re-installed 3.3.2 from the LibreOffice ppa. Although there were no errors on installation, LibreOffice now does not show in Applications/Office. Is there a way of updating the menu to show the applications without having to manually add them all again? I'm using 10.10

Any help would be appreciated.

---

### Post by timgood on 2011-06-06
Managed to reset the Applications menu by:

```
rm -rf .config/menus
``` and then ```
find ~/ -name "*.desktop" -delete 
```which set the menu back to default.

---

