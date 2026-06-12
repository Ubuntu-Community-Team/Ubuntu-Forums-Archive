---
title: "how can i reset plymouth"
date: 2010-09-05
forum: General Help
---

### Post by sxmaxchine on 2010-09-05
Hello the default ubuntu plymouth theme looked like it was realy small and stretched and made it look weird. anyway i tried to fix that problem by installing another theme [This theme]("http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696&PHPSESSID=b8ea4a898888967837889fa0412483ee")

now when i reboot my computer it is still small and stretched and the colours are not correct.

How can i reset plymouth to how it was by default.

---

### Post by sxmaxchine on 2010-09-05
I have fixed my resolution problem and changed the theme to another theme i downloaded. Now my problem is with colour. There are random colours all through the screen, how can i fix this.

---

### Post by dcstar on 2010-09-06
> **sxmaxchine said:**
> Hello the default ubuntu plymouth theme looked like it was realy small and stretched and made it look weird. anyway i tried to fix that problem by installing another theme [This theme]("http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696&PHPSESSID=b8ea4a898888967837889fa0412483ee")

now when i reboot my computer it is still small and stretched and the colours are not correct.

How can i reset plymouth to how it was by default.
Change the default.plymouth setting:
```
man update-alternatives
``` (I like to use the **galternatives** package)

---

