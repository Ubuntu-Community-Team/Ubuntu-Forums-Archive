---
title: "Commands to install on Ubuntu..."
date: 2010-05-16
forum: General Help
---

### Post by melrokz on 2010-05-16
I use Ubuntu desktop and server 10.04,
Is there a command that can install a standalone .deb package bringing in all it's dependencies?

---

### Post by darolu on 2010-05-16
dpkg?
[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

Usage:
```
$ man dpkg
```

---

### Post by iponeverything on 2010-05-16
```

dpkg -i <package>

```

Will install a deb that you already have. 

To download the package and pull in all the decencies for it use apt-get.

```
apt-get install <package>
```

---

### Post by rjcroy on 2010-05-16
I am not sure that dpkg handles dependencies. I have tried that before with a .deb and dependencies were not got! Instead I ended up double clicking on the .deb in nautilus, and the graphical installer handled it--but
If you are using a console I would try using aptitude

```
aptitude install <package>
```

---

### Post by TironN on 2010-05-16
> **rjcroy said:**
> I am not sure that dpkg handles dependencies. I have tried that before with a .deb and dependencies were not got! Instead I ended up double clicking on the .deb in nautilus, and the graphical installer handled it--but
If you are using a console I would try using aptitude

```
aptitude install <package>
```

DKPg doesn't directly handle dependencies but will give you a not found. Then you can apt-get the not found

---

### Post by ramjet_1953 on 2010-05-16
This command will often work to satisfy dependencies:

```
sudo apt-get build-dep <application>
```

Regards,
Roger :)

---

