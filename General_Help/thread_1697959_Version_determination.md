---
title: "Version determination"
date: 2011-03-01
forum: General Help
---

### Post by Diametric on 2011-03-01
How, via the CLI can I determine what version of Ubuntu I am running?

---

### Post by ean5533 on 2011-03-01
```
uname -a
```

---

### Post by Diametric on 2011-03-01
Thanks!

---

### Post by Rubi1200 on 2011-03-01
Alternatively,

```
cat /etc/*release
```

---

### Post by Diametric on 2011-03-01
> **Rubi1200 said:**
> Alternatively,

```
cat /etc/*release
```

That worked better.  The uname -a command only gives the kernal version and other info, but not which version of Ubuntu is installed.  

Thank you both!

---

### Post by Rubi1200 on 2011-03-02
No problem, you are more than welcome :-)

---

