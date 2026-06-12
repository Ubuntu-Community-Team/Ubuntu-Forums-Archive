---
title: "Computer won't restart. Hangs, have to hard reset"
date: 2009-08-17
forum: General Help
---

### Post by errolgreer on 2009-08-17
Hi. When I select 'restart' from Ubuntu it closes down Ubuntu, but then hangs with a black screen, until I do a hard reset. This is a multiboot system with XP, Vista, Win7 RC1 and Ubuntu. The other systems all restart normally and bring me back to the system choice menu.

---

### Post by cholericfun on 2009-08-17
try rebooting / shutting down via the terminal:
```

sudo shutdown -r now 
```  
for restart

and```


sudo shutdown -hP now
```
for shutdown

and see if at least these work fine.

---

### Post by errolgreer on 2009-08-24
Unfortunately this does not work. I seem to remember that there is a way to fix this problem which I had on an earlier version of Ubuntu, but I cannot remember how !


> **cholericfun said:**
> try rebooting / shutting down via the terminal:
```

sudo shutdown -r now 
```  
for restart

and```


sudo shutdown -hP now
```
for shutdown

and see if at least these work fine.

---

