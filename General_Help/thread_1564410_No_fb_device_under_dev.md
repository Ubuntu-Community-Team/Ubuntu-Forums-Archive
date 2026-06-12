---
title: "No fb device under /dev/"
date: 2010-08-30
forum: General Help
---

### Post by fai1224 on 2010-08-30
Does anyone know why there is no fb device under /dev/ ?
If there are some missing modules, please tell me what is the name of the modules.

The main problem is:  dmesg | grep fb
omapfb omapfb: failed to allocate framebuffer
omapfb omapfb: failed to allocate fbmem
omapfb omapfb: failed to setup omapfb
omapfb: probe of omapfb failed with error -12

---

