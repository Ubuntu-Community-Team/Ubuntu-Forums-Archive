---
title: "gambas 3.3.3"
date: 2012-10-10
forum: General Help
---

### Post by conradin on 2012-10-10
Hi All,
I was excited that gambas 3.3.3 came out today, but Im having trouble with the installation. 
I get this error when running a setup script.
```
~/trunk$ ./reconf-all 
./reconf-all: 7: libtoolize: not found
./reconf-all: 8: autoreconf: not found

```
can anyone get this software to work?
I find the documentation to be a little hard to read. 
Its better than when it was all spanish but I never had problems installing then either. Im using Lucid Lynx.

---

### Post by conradin on 2012-10-11
Ok, so in the list of dependencies on the gambas site, 
there is some error,
[http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)
 or problem with libgdk-pixbuf2.0-dev
not being the right name or something. 
I used synaptic to get the hopefully related files for pixbuf, though none of them had that exact name. 
./reconf-all 
seems to be working now.
The install version says 3.3.9 .... not sure about that one.

---

