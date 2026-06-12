---
title: "Can't uninstall firefox."
date: 2009-07-01
forum: General Help
---

### Post by CastilleV on 2009-07-01
Hey, I tried removing firefox using:
```

sudo apt-remove firefox

```
And its still installed.
I checked synaptic package manager and it showed it as uninstalled, but I am still on it, I can provide screenshots, if need be.

---

### Post by credobyte on 2009-07-01
```
sudo apt-get remove --purge firefox

```

---

### Post by CastilleV on 2009-07-01
No luck, its still installed. :\

---

### Post by credobyte on 2009-07-01
> **CastilleV said:**
> No luck, its still installed. :\

What you mean by "it's still installed" ? You can still use it ? Or simply .. you see an icon ?

---

### Post by CastilleV on 2009-07-01
> **credobyte said:**
> What you mean by "it's still installed" ? You can still use it ? Or simply .. you see an icon ?

I can still use it, I even tried logging out, then back in.

---

### Post by colau on 2009-07-01
> **CastilleV said:**
> I can still use it, I even tried logging out, then back in.
```

sudo aptitude purge firefox

```

---

### Post by CastilleV on 2009-07-01
> **colau said:**
> ```

sudo aptitude purge firefox

```

Its still here. 
I even has my directories still installed.
I checked using 
```

whereis firefox

```

---

### Post by colau on 2009-07-01
> **CastilleV said:**
> Its still here. 
I even has my directories still installed.
I checked using 
```

whereis firefox

```
After this
```

sudo aptitude purge firefox

```
Did you find any message in terminal?

---

### Post by CastilleV on 2009-07-01
> **colau said:**
> After this
```

sudo aptitude purge firefox

```
Did you find any message in terminal?

Nope.
Just said "castillev@castille-laptop:~$"

---

### Post by Soul-Sing on 2009-07-01
Did you install the new firefox 3.5 next to the "normal" firefox 3?

---

### Post by CastilleV on 2009-07-01
> **leoquant said:**
> Did you install the new firefox 3.5 next to the "normal" firefox 3?

Nope.

---

### Post by moster on 2009-07-01
actually firefox3 is removed by running
```
sudo apt-get remove firefox-3.0
```

I remove it today like this. Try it and say how it go.

---

