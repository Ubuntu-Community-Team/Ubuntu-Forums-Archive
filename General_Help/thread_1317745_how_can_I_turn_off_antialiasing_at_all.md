---
title: "how can I turn off antialiasing at all?"
date: 2009-11-07
forum: General Help
---

### Post by om zanka on 2009-11-07
how can I turn antialiasing off on fresh installed 9.10? for all font types

---

### Post by garvinrick4 on 2009-11-07
Looks like they have bit mapped fonts selection in preferences/appereance/fonts
Have four selections the monochrome fonts look bit mappaed to me. Browsers have
there own selections. Do not believe ever seen one selection for bit mapped fonts for
desktop and http pages all in one setting. Bit mapped fonts are not to pretty but beauty
is in the eye. You no what I mean.

---

### Post by kerry_s on 2009-11-07
> **om zanka said:**
> how can I turn antialiasing off on fresh installed 9.10? for all font types

settings-> user interface
uncheck antialiasing

---

### Post by om zanka on 2009-11-07
> **om zanka said:**
> how can I turn antialiasing off on fresh installed 9.10? for all font types

```
sudo rm /etc/fonts/conf.d/10-antialias.conf
sudo dpkg-reconfigure fontconfig

```

is the answer

---

