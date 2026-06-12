---
title: "Essential packages having to do with compiling and 'make'"
date: 2012-09-08
forum: General Help
---

### Post by nothreat33 on 2012-09-08
Hello, It's been a long time since I've used ubuntu. I'm trying to install a program but I'm getting some issues during make. I remember there being some essential packages you used to have to install. 

Things like build-essentials (which i can't find anymore)
and other essential libraries to ensure you can compile and run make successfully for a variety of things.

---

### Post by oldos2er on 2012-09-08
It's build-essential: ```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by SeijiSensei on 2012-09-08
Another useful apt-get option is "build-dep".  If you are building a version of a package that already exists for Ubuntu, mplayer for instance, you can run a command like 

```
sudo apt-get build-dep mplayer
```

and apt will install any dependencies like header files and libraries that will be needed to compile the targeted package.

---

