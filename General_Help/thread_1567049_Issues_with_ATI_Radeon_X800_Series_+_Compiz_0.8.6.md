---
title: "Issues with ATI Radeon X800 Series + Compiz 0.8.6"
date: 2010-09-03
forum: General Help
---

### Post by khmelnov.roman on 2010-09-03
Hello everyone.

I have a issue:
ATI Radeon X800 Series videocard works very bad with Compiz in 10.04.
Effects are **extremely** slow.
I've tried standart Mesa drivers and Gallium:
```
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on R430
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
```and tested various options in ccsm, but ineffectually...

Any ideas, how to fix that?

---

### Post by Mark Phelps on 2010-09-03
Basically, you're stuck using the open-source drivers because ATI dropped proprietary Linux driver support for your card nearly two years ago.

You might try booting a LiveCD of 10.10.  Even though it's till in Alpha stage, I've heard that they have improved the ATI open-source driver support in that version.

---

### Post by dudlas on 2010-09-03
try alt+f2. compiz --replace --indirect-rendering

---

### Post by khmelnov.roman on 2010-09-03
> **dudlas said:**
> try alt+f2. compiz --replace --indirect-rendering
O_o so simple, but **it** **works**!
Thanks!

---

