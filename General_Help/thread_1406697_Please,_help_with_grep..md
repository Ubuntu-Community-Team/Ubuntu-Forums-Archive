---
title: "Please, help with grep."
date: 2010-02-14
forum: General Help
---

### Post by GamePad64 on 2010-02-14
I try to find out, which packages a .deb package depends on. The best way to do it:

dpkg-deb -f <package.deb> Depends | grep -o "<regexp>"

What regular expression should I write to match Dependencies perfectly?

**upd:** Or is there any other way to do it?

---

### Post by Rocket2DMn on 2010-02-14
If you are installing something from a repository (official or otherwise) you can simply run
```
apt-cache depends <packagename>
```
e.g.
```
apt-cache depends pidgin
```

Are you trying to install something manually?  If so, the page you got it at should tell you what it depends on.

Otherwise, something like this might work:
```
dpkg-deb -f <package.deb> Depends | sed 's/, /\n/g'
```
Or for just the package:
```
dpkg-deb -f <package.deb> Depends | sed 's/, /\n/g' | awk '{print $1}'
```

---

