---
title: "Installing GCC, first day with ubuntu"
date: 2010-03-14
forum: General Help
---

### Post by granthays on 2010-03-14
I just got Ubuntu on a really old Dell Inspirion 8000 and I need gcc for programming classes.
 
When I ran the package install off the Ubuntu 9.10 disk it says:
 
"Error: Dependency is not satisfiable: gcc-4.4-base (= 4.4.1-4ubuntu8 )
 
Any ideas? Thanks!

---

### Post by hhh on 2010-03-14
Install the package gcc-4.4-base via Synaptic Package Manager (System>Administration>Synaptic Package Manager>put gcc-4.4-base in the Search field, mark it for installation and apply) or via a terminal (sudo apt-get install gcc-4.4-base).

HTH

---

### Post by GregBrannon on 2010-03-14
In a terminal window, try:

```
sudo apt-get install build-essential
```

That should give you all you need and some extra that you might not need now but will later.

---

