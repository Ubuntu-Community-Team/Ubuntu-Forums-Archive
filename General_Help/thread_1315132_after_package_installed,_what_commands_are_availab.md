---
title: "after package installed, what commands are available?"
date: 2009-11-05
forum: General Help
---

### Post by cliffk on 2009-11-05
i think this is simple question...

after i install a package, how do i know what new shell commands are available? are any commands added to the gnome window menu bar? is this information provided with the package itself (maybe something like an apt-cache showpkg)?

---

### Post by soapBAR2 on 2009-11-05
Once installed, open a terminal,

```
man packagename
```

And if it's a GUI program, then yes, it should add itself to the menu in the appropriate category. If you need to read the manpage of the program without installing it, just google 

> man packagename

---

### Post by diesch on 2009-11-05
```
dpkg -L packagename
```
lists the files that a package contains.

```
dpkg -L screenlets|grep /bin/.
``` usually lists the program files.

---

### Post by cliffk on 2009-11-05
cool! thanks...
is there a way to go backwards? given a shell command, can i determine what package it came from?

---

### Post by diesch on 2009-11-05
```
dpkg -S /some/file
```
will tell you what package /some/file belongs to

---

### Post by cliffk on 2009-11-05
works. thanks. i also found a separate app called apt-file. it maintains its own cache separate from apt-get, so i'm not sure it's worth it because for the examples i tried, it returned the same answer as dpkg -S

---

### Post by diesch on 2009-11-05
apt-file is usually a bit faster and works with packages that are not installed, too. But it doesn't work for packages that are not in the repositories and for files that are e.g. moved by dpkg-divert.

---

