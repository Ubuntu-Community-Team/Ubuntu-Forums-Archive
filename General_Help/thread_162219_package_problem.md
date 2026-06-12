---
title: "package problem"
date: 2006-04-18
forum: General Help
---

### Post by IsKall on 2006-04-18
Hi guys! 

I recently tried to update with sudo apt-get update, and because of that I got a package "broken", but when I go to Edit -> Fix Broken Packages and apply, this error comes

the file Synaptic is trying to update: 
libbrlapi1 (version 3.7.2-2ubuntu1) will be installed

And the error msg:
E: /var/cache/apt/archives/libbrlapi1_3.7.2-2ubuntu1_i386.deb: trying to overwrite `/lib/libbrlapi.so.0.4', which is also in package libbrlapi

How can I fix this?

---

### Post by kwaanens on 2006-04-18
Just remove libbrlapi and then reinstall ubuntu-desktop

Just had the same problem, package libbrlapi1 should have released with a "replace libbrlapi" command

- Ketil

---

### Post by IsKall on 2006-04-18
thank you kwaanens, it seems to work now :)

---

