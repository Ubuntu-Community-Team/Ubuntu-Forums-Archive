---
title: "how come I don't have the make command?"
date: 2006-03-18
forum: General Help
---

### Post by Patrick-Ruff on 2006-03-18
how come I don't have the make command? i.e. make install, make check etc.
it says command not found and all that.


.

---

### Post by Seth on 2006-03-18
You need to install the **build-essential** package :)

---

### Post by Ramses de Norre on 2006-03-18
```
sudo apt-get install build-essential
```

---

### Post by Steve1961 on 2006-03-18
[QUOTE=Patrick-Ruff]how come I don't have the make command? i.e. make install, make check etc.
it says command not found and all that.


.[/QUOTE]


Have you installed the build-essential package?

Oops, looks like we all replied at once

---

### Post by Patrick-Ruff on 2006-03-18
any way I can get it without being online? (I can't exactly get online at the moment unless one of you can crack up a key for linuxant modem drivers ;) which I doubt anyone will so)

---

### Post by Ramses de Norre on 2006-03-18
I don't think so, there are quiet a lot of apps in that package.

---

### Post by jerrykenny on 2006-03-18
Isnt "make" on the install cd ?   if you disable all the network repos in Synaptic, then update, then install make it aught to ask you put in the install cd then  . . . . .

---

