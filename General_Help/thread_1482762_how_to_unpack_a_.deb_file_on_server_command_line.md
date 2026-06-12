---
title: "how to unpack a *.deb file on server command line"
date: 2010-05-13
forum: General Help
---

### Post by AresArtemis1 on 2010-05-13
hi, friends, how to unpack a .deb file on server, I tried tar, but doesn't work

---

### Post by WorMzy on 2010-05-13
Do you need to unpack it or install it?

To install, run 'sudo dpkg -i /path/to/the/file.deb', to unpack use 'dpkg --unpack /path/to/the/file.deb'

---

### Post by AresArtemis1 on 2010-05-13
> **WorMzy said:**
> Do you need to unpack it or install it?

To install, run 'sudo dpkg -i /path/to/the/file.deb', to unpack use 'sudo dpkg --unpack /path/to/the/file.deb'
hi, I put command sudo dpkg - unpack file.deb

server say need an action option

help

---

### Post by DeMus on 2010-05-13
> **AresArtemis1 said:**
> hi, I put command sudo dpkg - unpack file.deb

server say need an action option

help

Type:
```
dpkg --unpack name.deb
```

That is with two minus sign ( -- )

---

### Post by 3rdalbum on 2010-05-14
> **AresArtemis1 said:**
> hi, I put command sudo dpkg - unpack file.deb

Try re-reading the answer given to you:

```
sudo dpkg -i file.deb
```

You're missing an i.

---

