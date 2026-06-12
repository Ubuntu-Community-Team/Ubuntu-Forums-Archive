---
title: "Downgrading sun-java6-jre/bin/plugin to 5 - Problems ensue"
date: 2009-11-14
forum: General Help
---

### Post by SouthOfHell on 2009-11-14
Hey I play an online java game and I want to try something out, I'm trying to downgrade java from 6 to 5.  I removed all the java6 files installed (jre/bin/plugin), and got the sun-java5 debs from the Hardy package site (I'm using Karmic however).

After downloading the debs, I'm faced with these messges:

Trying to install sun-java5-bin:
```
Error: Dependency is not satisfiable: sun-java5-jre (= 1.5.0-15-0ubuntu1)
```

So... I try sun-java5-jre and get:

```
Error: Dependency is not satisfiable: sun-java5-bin (= 1.5.0-15-0ubuntu1)|ia32-sun-java5-bin (= 1.5.0-15-0ubuntu1)
```

A bit confused here, how do I go about installing these debs?

---

### Post by mikewhatever on 2009-11-14
You can't freely move deb files from one release to another, some times it may work, and sometimes it won't, for example because of dependency problem. What exactly was wrong with Java6?

---

