---
title: "GCC not found"
date: 2006-02-12
forum: General Help
---

### Post by Mishal on 2006-02-12
Whatever software I try to install outside Synaptic, configure checks for gcc and fails to find it. But I have checked it in Synaptic and it shows that I have the latest gcc installed. A version of 4.x.x to be precise. Then why can't the gcc be found?:(

---

### Post by alfonz on 2006-02-12
some apps use older verions of gcc me thinks that one cause for your problem.

---

### Post by SWAT on 2006-02-12
[QUOTE=alfonz]some apps use older verions of gcc me thinks that one cause for your problem.[/QUOTE]
Yes, this could be the problem. Remember to READ the install instruction/requirements for the application. Try to also install gcc-3.4, maybe that will fix it

---

### Post by Mustard on 2006-02-12
Before you start compiling stuff outside the repositories you need to install the build-essential package...

```
sudo apt-get install build-essential
```

---

### Post by xerophyte on 2006-02-12
and 
```

 sudo apt-get install gcc-3.4

```
for me  build-essential missed the gcc-3.4

---

