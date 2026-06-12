---
title: "Places folder opens USC?"
date: 2011-10-24
forum: General Help
---

### Post by gippeswyc on 2011-10-24
version 11.10 - access to my folders **via places on the menu bar** **just launches the "ubuntu software centre". **The folders are there but not through Places.
Is this one of the stranger bugs?

---

### Post by uRock on 2011-10-24
bump for move to its own thread. The previous thread is for sharing known workarounds for bugs.

---

### Post by mc4man on 2011-10-24
Post what's in this file, easy to fix the file
```
gedit ~/.local/share/applications/mimeapps.list
```

Or you can just browse there & delete mimeapps.list
```
nautilus ~/.local/share/applications/
```

Here's my  bug on this - don't expect there will be anything done...
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

---

### Post by gippeswyc on 2011-10-25
> **mc4man said:**
> Post what's in this file, easy to fix the file
```
gedit ~/.local/share/applications/mimeapps.list
```Or you can just browse there & delete mimeapps.list
```
nautilus ~/.local/share/applications/
```Here's my  bug on this - don't expect there will be anything done...
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

Thanks mc4man... renamed the file and Places works fine now :)

---

