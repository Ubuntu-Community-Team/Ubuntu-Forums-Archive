---
title: "version information"
date: 2010-04-15
forum: General Help
---

### Post by akssps011 on 2010-04-15
How do I determine which kde and Qt version i have on my system.
i am using kde 9.10.

Thanks

---

### Post by linden940 on 2010-04-15
system > about 

there should be to listed..that will give or..SHOULD give you all the info you need

---

### Post by Chris Musampa on 2010-04-15
```
kde-config --version

```

---

### Post by akssps011 on 2010-04-16
Thanks. it worked. How can i update my Qt version.
Actaully I want to use qmake. but it says qmake is not installed

The kde-config --version gives
Qt: 3.3.8b
KDE: 3.5.10
kde-config: 1.0

---

### Post by Chris Musampa on 2010-04-16
> **akssps011 said:**
> Thanks. it worked. How can i update my Qt version.
Actaully I want to use qmake. but it says qmake is not installed

The kde-config --version gives
Qt: 3.3.8b
KDE: 3.5.10
kde-config: 1.0

Oops I just looked at your output, as you're using jaunty I assume you're on KDE4, I should've put:
```
kde4-config --version
```

---

### Post by akssps011 on 2010-04-16
thanks..worked.

---

