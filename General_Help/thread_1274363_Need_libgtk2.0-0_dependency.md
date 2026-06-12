---
title: "Need libgtk2.0-0 dependency"
date: 2009-09-24
forum: General Help
---

### Post by Dai777 on 2009-09-24
Where can I get the dependency libgtk2.0-0 from I need it to install imagination_2.0~beta1-1~getdeb1_i386.deb on hardy heron version of ubuntu.

---

### Post by jerrrys on 2009-09-24
its in synaptic

---

### Post by Dai777 on 2009-09-24
> **jerrrys said:**
> its in synaptic

Still getting the error message:
Dependency is not satisfiable:libgtk2.0-0
so it won't install. any help would be appreciated.

---

### Post by Darkwing-Duck on 2009-09-24
Try purging it from apt and then reinstalling it again.
 
```
sudo apt-get purge libgtk2.0-0
```
 
Then.
 
```
sudo apt-get install libgtk2.0-0
```
 
See if that does the trick for you.

---

### Post by Dai777 on 2009-09-24
> **Darkwing-Duck said:**
> Try purging it from apt and then reinstalling it again.
 
```
sudo apt-get purge libgtk2.0-0
```
 
Then.
 
```
sudo apt-get install libgtk2.0-0
```
 
See if that does the trick for you.

still getting the same error

---

### Post by Dai777 on 2009-09-24
Imagination requires gtk 2.14. I'm not sure if Ubuntu 8.04 is shipped
with that release.

Bye
Giuseppe

just had this reply from the developer, so this is probably why.

---

### Post by mc4man on 2009-09-24
> sudo apt-get purge libgtk2.0-0
Generally that is a very poor suggestion, did you take a look at what will get uninstalled along with libgtk2.0-0?

How much gets re-installed along with libgtk2.0-0 i'm not sure and not inclined to see.

(the Imagination package on getdebs has been built  for jaunty

---

### Post by Dai777 on 2009-09-25
> **mc4man said:**
> Generally that is a very poor suggestion, did you take a look at what will get uninstalled along with libgtk2.0-0?

How much gets re-installed along with libgtk2.0-0 i'm not sure and not inclined to see.

(the Imagination package on getdebs has been built  for jaunty

pity it looks a nice programme.

---

