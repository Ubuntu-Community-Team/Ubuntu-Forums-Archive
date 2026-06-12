---
title: "OpenOffice don't show up!?"
date: 2009-11-19
forum: General Help
---

### Post by volter on 2009-11-19
I downloaded language package for OpenOffice  and after the installation the icons just disappear from the menu.
I don't know how to fix it? I thought to reinstall it but I don't know how to do it either.

---

### Post by emigrant on 2009-11-19
try this in terminal:

```

/usr/bin/ooffice 

```

---

### Post by emigrant on 2009-11-19
if it didn't work try this:

```

whereis ooffice

```

---

### Post by volter on 2009-11-19
for the first code the result is ```
/usr/lib/openoffice/program/soffice: 214: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 234: /usr/lib/openoffice/program/soffice.bin: not found

```

for the second ```
ooffice: /usr/bin/ooffice /usr/share/man/man1/ooffice.1.gz
```

---

### Post by emigrant on 2009-11-19
Open up System-> Administration-> Software Sources-> Third-Party tab-> Add... button.

URI: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/)
distribution: jaunty <or if you use karmic replace jaunty with karmic>
components: main


run update manager.

---

### Post by gradinaruvasile on 2009-11-19
Did you install the OpenOffice from the repositories or the one downloaded from the OO site?

---

### Post by volter on 2009-11-19
I removed openoffice by using ```
apt-get remove openoffice.org*
```
know I tried to install it from synaptic it say ```
openoffice.org:
 Depends: openoffice.org-writer2latex but it is not going to be installed

```

I tried to do like emigrant said and it didn't find any update.

---

### Post by volter on 2009-11-19
Ok I fixed that by using janitor.

---

