---
title: "Compiz-Fusion problems"
date: 2010-03-21
forum: General Help
---

### Post by QuaGon on 2010-03-21
i tried to apt-get compiz fusion... then i found out i probably already had it (9.10)... anyway when i try to change from Kwin to compiz, i get an error message saying compiz failed to start, reverting back to default window manager...


any ideas >.<

im thinking maybe i messed things up trying to install an already installed program ??

---

### Post by wannabegeek on 2010-03-21
I'm not very experienced to be honest, but I will add that if you want to purge the existing compiz-fusion 
you can use:
```
 sudo apt-get purge compiz-fusion 
```

btw: did you try to install as:
```
sudo apt-get install compiz-fusion
```

good luck,
wbg

---

### Post by n0dix on 2010-03-21
> **QuaGon said:**
> [...]
im thinking maybe i messed things up trying to install an already installed program ??

That's never happens to me. The problem you have refer to is because Kde have its own visual effects and cannot coexists Kwin and Compiz at the same time. Maybe [this]("http://ubuntuforums.org/showthread.php?t=1363412") give you and idea.

---

