---
title: "cleaning out build dependencies"
date: 2006-06-18
forum: General Help
---

### Post by mlind on 2006-06-18
If i need to build .deb package from provided source, I usually first need to install
bunch of dependencies using apt-get build-dep. The problem is that I'd like to
remove every single build dependency after the build process.

Aptitude doesn't seem to support build-dep parameter, and apt-get is retarted on
dependency tracking. Is there some easy way to do this without playing with
deborphan or deprecated debfoster ?

---

### Post by mlind on 2006-06-19
debfoster seems to work nicely, too bad aptitude doesn't seem to support build-dep
option..

---

