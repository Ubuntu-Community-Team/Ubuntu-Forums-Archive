---
title: "Remove forced package"
date: 2009-12-11
forum: General Help
---

### Post by Hesediel on 2009-12-11
I am on a 64 bit ubuntu so, i forced the installation of package AdbeRdr9.2-1_i386linux_enu.deb now how can i remove it? It does not appear on synaptic

---

### Post by bodhi.zazen on 2009-12-11
list your packages with 

```
dpkg -l | grep AdbeRdr
```

Then remove it with dpkg

```
sudo dpkg -r <insert package name from above command>
```

Most likely dpkg -r AdbeRdr

---

