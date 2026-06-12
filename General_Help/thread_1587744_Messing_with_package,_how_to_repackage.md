---
title: "Messing with package, how to repackage"
date: 2010-10-04
forum: General Help
---

### Post by J V on 2010-10-04
I just took a .deb file apart to mess with the control file (Incorrectly conflicts with other package)

How exactly do I put the control.tar.gz data.tar.gz and debian-binary files into a .deb again? It won't let me simply compress them so I'm guessing I need a cli tool...

---

### Post by sisco311 on 2010-10-04
You have to extract the control information files from  the package: **dpkg-deb -e**, then (re)build the package: **dpkg-deb -b**.

i.e.
```
ar x package-version.deb
dpkg-deb -e package-version.deb

```

```
dpkg-deb -b ./ new.package.deb
```

---

### Post by gandaran on 2010-10-04
> **J V said:**
> I just took a .deb file apart to mess with the control file (Incorrectly conflicts with other package)

How exactly do I put the control.tar.gz data.tar.gz and debian-binary files into a .deb again? It won't let me simply compress them so I'm guessing I need a cli tool...
try packin [http://sourceforge.net/projects/packin/](http://sourceforge.net/projects/packin/)
and don't worry about the control file, fill in the new data to your liking (like the dependencies), use only the extracted 'usr' folder to make the .deb package

---

### Post by J V on 2010-10-04
Well I made the package and it still won't work... grr... If anyone wants to help, see [http://ubuntuforums.org/showthread.php?p=9920452](http://ubuntuforums.org/showthread.php?p=9920452)

---

